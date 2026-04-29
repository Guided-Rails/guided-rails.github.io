---
title: "Give an icon-only button an accessible name with aria-label"
date: 2026-04-29
---

Every interactive element needs an **accessible name**: the text that assistive technology announces.

## The problem

A button without an accessible name is unusable and confusing to screen reader users.

```erb
<%= button_tag do %>
  <%= trash_icon %>
<% end %>
```

<figure class="my-6">
  <figcaption class="text-sm text-gray-600 mb-2">Try it (Tab to focus, then listen to your screen reader):</figcaption>
  <button type="button" class="p-2 rounded border border-gray-300 hover:bg-gray-100">
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
      <path d="M3 6h18M8 6V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2M5 6v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V6" />
    </svg>
  </button>
</figure>

<figure class="my-6">
  <figcaption class="text-sm text-gray-600 mb-2">VoiceOver on the button above:</figcaption>
  <audio controls src="/assets/audio/button-no-name.m4a" class="w-full"></audio>
  <p class="text-sm text-gray-600 mt-2"><em>Transcript: "button"</em></p>
</figure>

## The fix

Add an `aria-label` so the button's purpose is clear.

```erb
<%= button_tag "aria-label": "Delete item" do %>
  <%= trash_icon %>
<% end %>
```

<figure class="my-6">
  <figcaption class="text-sm text-gray-600 mb-2">Try it (Tab to focus, then listen to your screen reader):</figcaption>
  <button type="button" aria-label="Delete item" class="p-2 rounded border border-gray-300 hover:bg-gray-100">
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
      <path d="M3 6h18M8 6V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2M5 6v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V6" />
    </svg>
  </button>
</figure>

<figure class="my-6">
  <figcaption class="text-sm text-gray-600 mb-2">Now VoiceOver announces:</figcaption>
  <audio controls src="/assets/audio/button-with-name.m4a" class="w-full"></audio>
  <p class="text-sm text-gray-600 mt-2"><em>Transcript: "Delete item, button"</em></p>
</figure>

## Further reading

- [WCAG 4.1.2: Name, Role, Value](https://www.w3.org/WAI/WCAG22/Understanding/name-role-value.html)
- [ARIA APG: Providing Accessible Names and Descriptions](https://www.w3.org/WAI/ARIA/apg/practices/names-and-descriptions/)
