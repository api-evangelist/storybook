---
title: "Storybook MCP for React"
url: "https://storybook.js.org/blog/storybook-mcp-for-react/"
date: "Mon, 23 Mar 2026 16:51:40 GMT"
author: "Kyle Gach"
feed_url: "https://storybook.js.org/blog/rss"
---
<img alt="Storybook MCP for React" src="https://storage.ghost.io/c/f9/d7/f9d78a80-56f8-4adc-8ba1-0e2d6ee72b16/content/images/2026/03/Storybook-MCP-for-React.png" /><p>Agents don’t know anything about your components so they make up slop that doesn’t match your coding standards. <a href="https://storybook.js.org/ai?ref=storybookblog.ghost.io">Storybook MCP</a> gives agents intelligence and test guardrails to keep on track:</p><ol><li>Context about your existing components to reuse</li><li>Instructions to write stories and preview their work</li><li>Ability to run tests and fix their own issues</li></ol><figure class="kg-card kg-video-card kg-width-wide">
            <div class="kg-video-container">
                <video height="942" loop="" poster="https://img.spacergif.org/v1/1920x942/0a/spacer.png" preload="metadata" src="https://storage.ghost.io/c/f9/d7/f9d78a80-56f8-4adc-8ba1-0e2d6ee72b16/content/media/2026/03/Storybook-MCP-Hero.mp4" width="1920">
                <div class="kg-video-overlay">
                    <button class="kg-video-large-play-icon">
                        <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                            <path d="M23.14 10.608 2.253.164A1.559 1.559 0 0 0 0 1.557v20.887a1.558 1.558 0 0 0 2.253 1.392L23.14 13.393a1.557 1.557 0 0 0 0-2.785Z">
                        </svg>
                    </button>
                </div>
                <div class="kg-video-player-container kg-video-hide">
                    <div class="kg-video-player">
                        <button class="kg-video-play-icon">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <path d="M23.14 10.608 2.253.164A1.559 1.559 0 0 0 0 1.557v20.887a1.558 1.558 0 0 0 2.253 1.392L23.14 13.393a1.557 1.557 0 0 0 0-2.785Z">
                            </svg>
                        </button>
                        <button class="kg-video-pause-icon kg-video-hide">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <rect height="22" rx="1.5" ry="1.5" width="7" x="3" y="1">
                                <rect height="22" rx="1.5" ry="1.5" width="7" x="14" y="1">
                            </svg>
                        </button>
                        <span class="kg-video-current-time">0:00</span>
                        <div class="kg-video-time">
                            /<span class="kg-video-duration">0:19</span>
                        </div>
                        <input class="kg-video-seek-slider" max="100" type="range" value="0" />
                        <button class="kg-video-playback-rate">1×</button>
                        <button class="kg-video-unmute-icon">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <path d="M15.189 2.021a9.728 9.728 0 0 0-7.924 4.85.249.249 0 0 1-.221.133H5.25a3 3 0 0 0-3 3v2a3 3 0 0 0 3 3h1.794a.249.249 0 0 1 .221.133 9.73 9.73 0 0 0 7.924 4.85h.06a1 1 0 0 0 1-1V3.02a1 1 0 0 0-1.06-.998Z">
                            </svg>
                        </button>
                        <button class="kg-video-mute-icon kg-video-hide">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <path d="M16.177 4.3a.248.248 0 0 0 .073-.176v-1.1a1 1 0 0 0-1.061-1 9.728 9.728 0 0 0-7.924 4.85.249.249 0 0 1-.221.133H5.25a3 3 0 0 0-3 3v2a3 3 0 0 0 3 3h.114a.251.251 0 0 0 .177-.073ZM23.707 1.706A1 1 0 0 0 22.293.292l-22 22a1 1 0 0 0 0 1.414l.009.009a1 1 0 0 0 1.405-.009l6.63-6.631A.251.251 0 0 1 8.515 17a.245.245 0 0 1 .177.075 10.081 10.081 0 0 0 6.5 2.92 1 1 0 0 0 1.061-1V9.266a.247.247 0 0 1 .073-.176Z">
                            </svg>
                        </button>
                        <input class="kg-video-volume-slider" max="100" type="range" value="100" />
                    </div>
                </div>
            </div>
            
        </figure><div class="kg-card kg-callout-card kg-callout-card-blue"><div class="kg-callout-emoji">💁</div><div class="kg-callout-text"><b><strong style="white-space: pre-wrap;">“But what about skills?”</strong></b><br />We’re investing in both. Skills are a helpful way to teach agents how to accomplish tasks. But MCP is required for back-and-forth communication with agents to power self-healing testing. </div></div><h3 id="force-agents-to-use-your-components">Force agents to use your components</h3><p>Storybook MCP equips agents with component metadata like stories, API, and docs. This allows agents to reuse existing components instead of inventing new patterns. It does this faster and with fewer tokens compared to not using MCP.</p><figure class="kg-card kg-image-card kg-card-hascaption"><img alt="Storybook MCP for React" class="kg-image" height="802" src="https://storage.ghost.io/c/f9/d7/f9d78a80-56f8-4adc-8ba1-0e2d6ee72b16/content/images/2026/03/image-3.png" width="2000" /><figcaption><span style="white-space: pre-wrap;">Benchmarks from generating UI with the </span><a href="https://reshaped.so/?ref=storybookblog.ghost.io"><span style="white-space: pre-wrap;">Reshaped</span></a><span style="white-space: pre-wrap;"> component library, with and without Storybook MCP</span></figcaption></figure><h3 id="share-ui-context-across-teams">Share UI context across teams</h3><p>Teams often split their app and design system into separate Storybooks. To generate UI with components from more than one Storybook, you can use the MCP server together with <a href="https://storybook.js.org/docs/sharing/storybook-composition?ref=storybookblog.ghost.io" rel="noopener noreferrer">composition</a>. </p><figure class="kg-card kg-image-card kg-card-hascaption"><img alt="Storybook MCP for React" class="kg-image" height="1070" src="https://storage.ghost.io/c/f9/d7/f9d78a80-56f8-4adc-8ba1-0e2d6ee72b16/content/images/2026/03/Storybook-MCP-for-React--3-.png" width="2000" /><figcaption><span style="white-space: pre-wrap;">Agents can read data from composition without needing to connect with multiple endpoints.</span></figcaption></figure><p><strong>Publish remote MCP</strong><br />Publish your Storybook MCP server to share component context with your team without running Storybook locally. Teammates can add the published MCP to their agent, even if their project doesn’t use Storybook.</p><p>Chromatic supports <a href="https://www.chromatic.com/ai?ref=storybookblog.ghost.io">publishing Storybook MCP</a> out of the box for free. It also comes with quality checks, versioning, and secure authorization built-in.</p><h3 id="review-agent-work-with-story-previews">Review agent work with story previews</h3><p>When an agent is finished, it summarizes its work. Instead of a wall of text, Storybook MCP embeds live stories directly inside the chat UI. You can verify the look and feel of the generated UI, including interactions like hover states, without leaving the client. </p><figure class="kg-card kg-image-card kg-width-wide kg-card-hascaption"><img alt="Storybook MCP for React" class="kg-image" height="1269" src="https://storage.ghost.io/c/f9/d7/f9d78a80-56f8-4adc-8ba1-0e2d6ee72b16/content/images/2026/03/Snapshots-denied-3.png" width="2000" /><figcaption><span style="white-space: pre-wrap;">The live story is embedded directly in the agent chat interface via </span><a href="https://blog.modelcontextprotocol.io/posts/2025-11-21-mcp-apps/?ref=storybookblog.ghost.io"><span style="white-space: pre-wrap;">MCP Apps</span></a><span style="white-space: pre-wrap;">. A link to that story is also included for deeper inspection.</span></figcaption></figure><h3 id="agents-self-verify-with-tests">Agents self-verify with tests</h3><p>The MCP server gives your agent tools to run component and accessibility tests. It only tests what it deems relevant, making the feedback loop fast and focused. When the agent kicks off a test run, you see the results stream into Storybook's UI.</p><p>If there are errors, the agent applies fixes itself or alerts the developer when human judgement is needed.</p><figure class="kg-card kg-video-card kg-width-wide kg-card-hascaption">
            <div class="kg-video-container">
                <video height="1080" loop="" poster="https://img.spacergif.org/v1/1728x1080/0a/spacer.png" preload="metadata" src="https://storage.ghost.io/c/f9/d7/f9d78a80-56f8-4adc-8ba1-0e2d6ee72b16/content/media/2026/03/Code-1.mp4" width="1728">
                <div class="kg-video-overlay">
                    <button class="kg-video-large-play-icon">
                        <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                            <path d="M23.14 10.608 2.253.164A1.559 1.559 0 0 0 0 1.557v20.887a1.558 1.558 0 0 0 2.253 1.392L23.14 13.393a1.557 1.557 0 0 0 0-2.785Z">
                        </svg>
                    </button>
                </div>
                <div class="kg-video-player-container kg-video-hide">
                    <div class="kg-video-player">
                        <button class="kg-video-play-icon">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <path d="M23.14 10.608 2.253.164A1.559 1.559 0 0 0 0 1.557v20.887a1.558 1.558 0 0 0 2.253 1.392L23.14 13.393a1.557 1.557 0 0 0 0-2.785Z">
                            </svg>
                        </button>
                        <button class="kg-video-pause-icon kg-video-hide">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <rect height="22" rx="1.5" ry="1.5" width="7" x="3" y="1">
                                <rect height="22" rx="1.5" ry="1.5" width="7" x="14" y="1">
                            </svg>
                        </button>
                        <span class="kg-video-current-time">0:00</span>
                        <div class="kg-video-time">
                            /<span class="kg-video-duration">0:10</span>
                        </div>
                        <input class="kg-video-seek-slider" max="100" type="range" value="0" />
                        <button class="kg-video-playback-rate">1×</button>
                        <button class="kg-video-unmute-icon">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <path d="M15.189 2.021a9.728 9.728 0 0 0-7.924 4.85.249.249 0 0 1-.221.133H5.25a3 3 0 0 0-3 3v2a3 3 0 0 0 3 3h1.794a.249.249 0 0 1 .221.133 9.73 9.73 0 0 0 7.924 4.85h.06a1 1 0 0 0 1-1V3.02a1 1 0 0 0-1.06-.998Z">
                            </svg>
                        </button>
                        <button class="kg-video-mute-icon kg-video-hide">
                            <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                                <path d="M16.177 4.3a.248.248 0 0 0 .073-.176v-1.1a1 1 0 0 0-1.061-1 9.728 9.728 0 0 0-7.924 4.85.249.249 0 0 1-.221.133H5.25a3 3 0 0 0-3 3v2a3 3 0 0 0 3 3h.114a.251.251 0 0 0 .177-.073ZM23.707 1.706A1 1 0 0 0 22.293.292l-22 22a1 1 0 0 0 0 1.414l.009.009a1 1 0 0 0 1.405-.009l6.63-6.631A.251.251 0 0 1 8.515 17a.245.245 0 0 1 .177.075 10.081 10.081 0 0 0 6.5 2.92 1 1 0 0 0 1.061-1V9.266a.247.247 0 0 1 .073-.176Z">
                            </svg>
                        </button>
                        <input class="kg-video-volume-slider" max="100" type="range" value="100" />
                    </div>
                </div>
            </div>
            <figcaption><p><span style="white-space: pre-wrap;">The agent kicks off a test run, and you can see results appear in realtime in Storybook's UI</span></p></figcaption>
        </figure><h2 id="get-started">Get started</h2><p>Storybook MCP is available now in Storybook 10.3 for React projects. Try it now below or read the full <a href="https://storybook.js.org/docs/ai/mcp/overview?ref=storybookblog.ghost.io">installation docs</a>.<em> </em>MCP support for other frameworks coming later this year.</p><p>Upgrade to version 10.3+:</p><pre><code class="language-bash">npx storybook@latest upgrade
</code></pre><p>Install and register the addon:</p><pre><code class="language-bash">npx storybook add @storybook/addon-mcp
</code></pre><p>Add the MCP server to your client:</p><pre><code class="language-bash">npx mcp-add --type http --url "http://localhost:6006/mcp" --scope project
</code></pre>
