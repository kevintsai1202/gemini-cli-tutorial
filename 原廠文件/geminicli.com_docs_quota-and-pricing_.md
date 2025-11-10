---
url: "https://geminicli.com/docs/quota-and-pricing/"
title: "Gemini CLI: Quotas and Pricing | Gemini CLI"
---

[Skip to content](https://geminicli.com/docs/quota-and-pricing/#_top)

Are you seeing timeout (429) errors in Gemini CLI?
[We're on it.](https://github.com/google-gemini/gemini-cli/discussions/12311)

# Gemini CLI: Quotas and Pricing

Copy as MarkdownCopied!

Gemini CLI offers a generous free tier that covers the use cases for many
individual developers. For enterprise / professional usage, or if you need
higher limits, there are multiple possible avenues depending on what type of
account you use to authenticate.

See [privacy and terms](https://geminicli.com/docs/tos-privacy) for details on Privacy policy and
Terms of Service.

> \[!NOTE\]
>
> Published prices are list price; additional negotiated commercial discounting
> may apply.

This article outlines the specific quotas and pricing applicable to the Gemini
CLI when using different authentication methods.

Generally, there are three categories to choose from:

- Free Usage: Ideal for experimentation and light use.
- Paid Tier (fixed price): For individual developers or enterprises who need
more generous daily quotas and predictable costs.
- Pay-As-You-Go: The most flexible option for professional use, long-running
tasks, or when you need full control over your usage.

## Free Usage

[Section titled “Free Usage”](https://geminicli.com/docs/quota-and-pricing/#free-usage)

Your journey begins with a generous free tier, perfect for experimentation and
light use.

Your free usage limits depend on your authorization type.

### Log in with Google (Gemini Code Assist for individuals)

[Section titled “Log in with Google (Gemini Code Assist for individuals)”](https://geminicli.com/docs/quota-and-pricing/#log-in-with-google-gemini-code-assist-for-individuals)

For users who authenticate by using their Google account to access Gemini Code
Assist for individuals. This includes:

- 1000 model requests / user / day
- 60 model requests / user / minute
- Model requests will be made across the Gemini model family as determined by
Gemini CLI.

Learn more at
[Gemini Code Assist for Individuals Limits](https://developers.google.com/gemini-code-assist/resources/quotas#quotas-for-agent-mode-gemini-cli).

### Log in with Gemini API Key (Unpaid)

[Section titled “Log in with Gemini API Key (Unpaid)”](https://geminicli.com/docs/quota-and-pricing/#log-in-with-gemini-api-key-unpaid)

If you are using a Gemini API key, you can also benefit from a free tier. This
includes:

- 250 model requests / user / day
- 10 model requests / user / minute
- Model requests to Flash model only.

Learn more at
[Gemini API Rate Limits](https://ai.google.dev/gemini-api/docs/rate-limits).

### Log in with Vertex AI (Express Mode)

[Section titled “Log in with Vertex AI (Express Mode)”](https://geminicli.com/docs/quota-and-pricing/#log-in-with-vertex-ai-express-mode)

Vertex AI offers an Express Mode without the need to enable billing. This
includes:

- 90 days before you need to enable billing.
- Quotas and models are variable and specific to your account.

Learn more at
[Vertex AI Express Mode Limits](https://cloud.google.com/vertex-ai/generative-ai/docs/start/express-mode/overview#quotas).

## Paid tier: Higher limits for a fixed cost

[Section titled “Paid tier: Higher limits for a fixed cost”](https://geminicli.com/docs/quota-and-pricing/#paid-tier-higher-limits-for-a-fixed-cost)

If you use up your initial number of requests, you can continue to benefit from
Gemini CLI by upgrading to one of the following subscriptions:

- [Google AI Pro and AI Ultra](https://cloud.google.com/products/gemini/pricing)
by signing up at
[Set up Gemini Code Assist](https://goo.gle/set-up-gemini-code-assist). This
is recommended for individual developers. Quotas and pricing are based on a
fixed price subscription.

For predictable costs, you can log in with Google.

Learn more at
[Gemini Code Assist Quotas and Limits](https://developers.google.com/gemini-code-assist/resources/quotas)

- [Purchase a Gemini Code Assist Subscription through Google Cloud](https://cloud.google.com/gemini/docs/codeassist/overview)
by signing up in the Google Cloud console. Learn more at
[Set up Gemini Code Assist](https://cloud.google.com/gemini/docs/discover/set-up-gemini)
Quotas and pricing are based on a fixed price subscription with assigned
license seats. For predictable costs, you can sign in with Google.

This includes:


  - Gemini Code Assist Standard edition:
    - 1500 model requests / user / day
    - 120 model requests / user / minute
  - Gemini Code Assist Enterprise edition:
    - 2000 model requests / user / day
    - 120 model requests / user / minute
  - Model requests will be made across the Gemini model family as determined by
    Gemini CLI.

[Learn more about Gemini Code Assist Standard and Enterprise license limits](https://developers.google.com/gemini-code-assist/resources/quotas#quotas-for-agent-mode-gemini-cli).

## Pay As You Go

[Section titled “Pay As You Go”](https://geminicli.com/docs/quota-and-pricing/#pay-as-you-go)

If you hit your daily request limits or exhaust your Gemini Pro quota even after
upgrading, the most flexible solution is to switch to a pay-as-you-go model,
where you pay for the specific amount of processing you use. This is the
recommended path for uninterrupted access.

To do this, log in using a Gemini API key or Vertex AI.

- Vertex AI (Regular Mode):
  - Quota: Governed by a dynamic shared quota system or pre-purchased
    provisioned throughput.
  - Cost: Based on model and token usage.

Learn more at
[Vertex AI Dynamic Shared Quota](https://cloud.google.com/vertex-ai/generative-ai/docs/resources/dynamic-shared-quota)
and [Vertex AI Pricing](https://cloud.google.com/vertex-ai/pricing).

- Gemini API key:
  - Quota: Varies by pricing tier.
  - Cost: Varies by pricing tier and model/token usage.

Learn more at
[Gemini API Rate Limits](https://ai.google.dev/gemini-api/docs/rate-limits),
[Gemini API Pricing](https://ai.google.dev/gemini-api/docs/pricing)

It’s important to highlight that when using an API key, you pay per token/call.
This can be more expensive for many small calls with few tokens, but it’s the
only way to ensure your workflow isn’t interrupted by quota limits.

## Gemini for Workspace plans

[Section titled “Gemini for Workspace plans”](https://geminicli.com/docs/quota-and-pricing/#gemini-for-workspace-plans)

These plans currently apply only to the use of Gemini web-based products
provided by Google-based experiences (for example, the Gemini web app or the
Flow video editor). These plans do not apply to the API usage which powers the
Gemini CLI. Supporting these plans is under active consideration for future
support.

## Tips to Avoid High Costs

[Section titled “Tips to Avoid High Costs”](https://geminicli.com/docs/quota-and-pricing/#tips-to-avoid-high-costs)

When using a Pay as you Go API key, be mindful of your usage to avoid unexpected
costs.

- Don’t blindly accept every suggestion, especially for computationally
intensive tasks like refactoring large codebases.
- Be intentional with your prompts and commands. You are paying per call, so
think about the most efficient way to get the job done.

## Gemini API vs. Vertex

[Section titled “Gemini API vs. Vertex”](https://geminicli.com/docs/quota-and-pricing/#gemini-api-vs-vertex)

- Gemini API (gemini developer api): This is the fastest way to use the Gemini
models directly.
- Vertex AI: This is the enterprise-grade platform for building, deploying, and
managing Gemini models with specific security and control requirements.

## Understanding your usage

[Section titled “Understanding your usage”](https://geminicli.com/docs/quota-and-pricing/#understanding-your-usage)

A summary of model usage is available through the `/stats` command and presented
on exit at the end of a session.

This website uses [cookies](https://policies.google.com/technologies/cookies) from Google to deliver and enhance the quality of its services and to analyze
traffic.

I understand.