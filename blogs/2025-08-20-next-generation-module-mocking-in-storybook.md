---
title: "Next-generation module mocking in Storybook"
url: "https://storybook.js.org/blog/next-generation-module-mocking/"
date: "Wed, 20 Aug 2025 23:02:40 GMT"
author: "Valentin Palkovic"
feed_url: "https://storybook.js.org/blog/rss"
---
<img alt="Next-generation module mocking in Storybook" src="https://storage.ghost.io/c/f9/d7/f9d78a80-56f8-4adc-8ba1-0e2d6ee72b16/content/images/2025/08/Frame-1055-2.jpg" /><p>Consistency is the bedrock of developing and testing UI in isolation. Your Storybook stories should render the same UI every time, regardless of who is viewing them, when they're viewing them, or whether your backend services are online. The same input to your story should always produce identical output.</p><p>This is straightforward when your component's only input is props. For network data, the popular <a href="https://storybook.js.org/addons/msw-storybook-addon?ref=storybookblog.ghost.io">Mock Service Worker addon</a> is a fantastic solution. But what about other dependencies? How do you handle components that rely on browser APIs like <code>localStorage</code> or which require authentication to work?</p><p>Mocking these inputs has been a long-standing challenge. In Storybook 8.1, we introduced a <a href="https://storybook.js.org/blog/type-safe-module-mocking/?ref=storybookblog.ghost.io">standards-based approach using Subpath Imports</a>. While powerful, it required manual <code>package.json</code> configuration and changes to your component's import paths.</p><p>Today, we’re thrilled to introduce a next-generation solution that is simpler, more powerful, and offers a superior developer experience.</p><h2 id="introducing-sbmock">Introducing <code>sb.mock()</code></h2><p>The new module mocking feature is powered by Vitest's battle-tested mocking engine, but is deeply integrated into Storybook's workflow to work seamlessly for both <strong>Vite and Webpack</strong> in both <strong>dev and production</strong> modes.</p><p>It’s all centered around a new, intuitive API: <code>sb.mock()</code>.</p><p>Consider a user-configurable&nbsp;<code>Dashboard</code>&nbsp;component that allows the user to choose what information is shown and stores those settings in the browser’s local storage:</p><pre><code class="language-ts">// lib/settings.ts
export const getDashboardLayout = () =&gt; {
  const layout = window.localStorage.getItem('dashboard.layout');
  return layout ? JSON.parse(layout) : [];
};

// components/Dashboard.tsx
import { getDashboardLayout } from '../lib/settings.ts';

export const Dashboard = () =&gt; {
  const layout = getDashboardLayout();
  // ...logic to display layout
};</code></pre><p>Now, you can mock it globally for all your stories with a single line in your <code>.storybook/preview.ts</code> file:</p><pre><code class="language-ts">// .storybook/preview.ts
import { sb } from 'storybook/test';

// That's it! The settings module will now be mocked in all stories.
sb.mock('../lib/settings.ts');</code></pre><p>This approach is cleaner, requires no changes to your component code, and is completely type-safe.</p><h2 id="how-to-use-automocking">How to use automocking</h2><p>The <code>sb.mock()</code> API is designed to be flexible and cover all your mocking needs directly from your preview configuration.</p><h3 id="automocking-without-mock-files">Automocking without mock files</h3><p>For a majority of cases, you can use the automatically generated mocks. If you call <code>sb.mock('...', { spy: true })</code>, Storybook will replace all exports with spies that call the original functions while recording every interaction. This allows you to continue using the original behavior (or modify it, as needed) and track its usage.</p><pre><code class="language-ts">// .storybook/preview.ts
import { sb } from 'storybook/test';

sb.mock('../lib/analytics.ts', { spy: true });</code></pre><p>Now, in your stories, you can import from the original path and either use the original functionality or configure the mock for that specific story. This colocates the mock’s behavior with where it is used.</p><pre><code class="language-ts">// components/Dashboard.stories.ts
import { mocked } from 'storybook/test';
import { trackEvent } from '../lib/analytics.ts';

export const MyStory = {
  beforeEach: () =&gt; {
    /*
     * The `trackEvent` function is already a mock!
     * The `mocked` utility is just for proper mock function types
     */
    mocked(trackEvent).mockResolvedValue({ status: 'ok' });
  },
  play: async () =&gt; {
    // ... interact with the component
    await expect(trackEvent).toHaveBeenCalledWith('dashboard-viewed');
  },
};</code></pre><h3 id="replacing-modules">Replacing modules</h3><p>If you set <code>spy</code> to <code>false</code> (or omit it), Storybook automatically mocks the module by replacing its exports with safe, inert values. Functions and class instances are replaced with empty mocks (<code>vi.fn()</code>), arrays are emptied, objects are deeply cloned, and primitives are kept as-is. This gives you a clean slate to work with in every story.</p><pre><code class="language-ts">// .storybook/preview.ts
import { sb } from 'storybook/test';

sb.mock('../lib/analytics.ts');
</code></pre><h3 id="automocking-with-mocks">Automocking with <code>__mocks__</code></h3><p>If a file exists in a <code>__mocks__</code> directory adjacent to the original module, Storybook will automatically use it. This convention, popularized by Jest and Vitest, is perfect for more complex modules that need dedicated mock implementations. It also ensures that the original functionality is never executed, which can be important when mocking things like server code in a browser environment.</p><p><strong>For local modules</strong>, place the <code>__mocks__</code> directory adjacent to the original module:</p><pre><code class="language-txt">src/
├── lib/
│   ├── __mocks__/
│   │   └── analytics.ts  // This mock will be used automatically
│   └── analytics.ts      // The original module
└── components/
    └── Dashboard.tsx
</code></pre><pre><code class="language-ts">// src/lib/__mocks__/analytics.ts
// A custom mock implementation for all stories
export const trackEvent = async () =&gt; {
  return { status: 'ok' };
};
</code></pre><p><strong>For <code>node_modules</code></strong>, create a <code>__mocks__</code> directory in your project's root. Inside, create a file named after the package you want to mock. For deep imports, replicate the folder structure.</p><pre><code class="language-js">// project-root/__mocks__/lodash-es.js
export default {
  VERSION: 'mocked!',
};

// project-root/__mocks__/lodash-es/add.js
export default (a, b) =&gt; 'mocked add';
</code></pre><p>Then, register the mock in your Storybook preview config:</p><pre><code class="language- ts">// .storybook/preview.ts
import { sb } from 'storybook/test';

sb.mock('../src/lib/analytics.ts');
sb.mock('lodash-es');
sb.mock('lodash-es/add');</code></pre><p>Currently, we only support mocking ES Modules. Mocking CommonJS modules is not supported.</p><h3 id="type-safe-mocking-with-import">Type-safe mocking with <code>import()</code></h3><p>To improve developer experience and prevent broken paths, <code>sb.mock</code> also accepts a dynamic <code>import()</code> statement. This gives you full TypeScript support and IDE autocompletion, ensuring that if you refactor or move a file, your mock paths will be updated automatically.</p><pre><code class="language-ts">// .storybook/preview.ts
import { sb } from 'storybook/test';

// ✅ Type-safe, refactor-friendly, and recommended!
sb.mock(import('../lib/analytics.ts'));
</code></pre><p>Under the hood, Storybook still operates on the string path, but this syntax provides a superior authoring experience. Note that any aliased paths are not supported within the <code>import()</code> statement.</p><h2 id="how-it-works-ahead-of-time-transformation">How it works: Ahead-of-time transformation</h2><p>The magic behind <code>sb.mock()</code> is a powerful <strong>Ahead-of-Time (AOT)</strong> transformation strategy. Unlike our previous approach that manipulated <code>package.json</code>, this new system integrates directly with your bundler.</p><p>During startup, custom Vite and Webpack plugins scan your <code>.storybook/preview.ts</code> file for all <code>sb.mock()</code> calls. They then intelligently rewrite your application's dependency graph <em>before</em> it's served to the browser or bundled for production.</p><p>This means the final code that runs in the browser already has the mocked modules baked in. This approach is:</p><ul><li><strong>Performant</strong>: There is zero runtime overhead.</li><li><strong>Robust</strong>: It works identically in dev mode and in static production builds.</li><li><strong>Simple</strong>: It requires no complex client-side interception or Service Workers.</li></ul><h3 id="comparison-to-other-mocking-solutions">Comparison to other mocking solutions</h3><p>This new API offers a clear improvement over our previous approach and provides a focused alternative to general-purpose testing tools.</p><ul><li><strong>vs. old subpath imports</strong>: The new API is a major leap forward. You no longer need to modify <code>package.json</code>, change your component import paths, or create boilerplate <code>.mock.ts</code> files.</li><li><strong>vs. Vitest</strong>: While powered by Vitest's engine, the Storybook implementation is tailored for component isolation.<ul><li><strong>Global scope</strong>: Mocks are defined globally in <code>preview.ts</code> and apply to all stories.</li><li><strong>No factory functions</strong>: The API does not accept a runtime factory (e.g., <code>sb.mock('path', () =&gt; ({}))</code>) to ensure reliability in static builds. For complex mocks, use the <code>__mocks__</code> directory.</li><li><strong>Static by design</strong>: The system is intentionally static to guarantee consistency between development and production builds.</li></ul></li></ul><h2 id="try-it-today">Try it today</h2><p>Module mocking is available in <strong>Storybook 9.1</strong>. To get started, upgrade your project:</p><pre><code class="language-bash">npx storybook@latest upgrade
</code></pre><p>To learn more, check out the full examples and API details in the <a href="https://storybook.js.org/docs/writing-stories/mocking-data-and-modules/mocking-modules?ref=storybookblog.ghost.io" rel="noreferrer"><strong>Storybook documentation</strong></a>. We can't wait to see what you build!</p><figure class="kg-card kg-embed-card"><blockquote class="bluesky-embed"><p lang="en">Testing components that depend on things like localStorage or authentication can be tricky. Storybook makes it easy with our new module mocking API built on top of @vitest.dev's excellent mocking tools.

storybook.js.org/blog/next-ge...</p>— <a href="https://bsky.app/profile/did:plc:osfpupzlwycyr6dxic6adh7t?ref_src=embed&amp;ref=storybookblog.ghost.io">Storybook (@storybook.js.org)</a> <a href="https://bsky.app/profile/did:plc:osfpupzlwycyr6dxic6adh7t/post/3lwwji2agw22o?ref_src=embed&amp;ref=storybookblog.ghost.io">2025-08-21T18:00:06.677Z</a></blockquote></figure>
