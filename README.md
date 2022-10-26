# Sveltekit dark mode example

A simple example of switching between light and dark modes using Sveltekit. This example should:

- Use OS/browser preference
- Allow overriding native setting
- Store preference in local storage

I haven't given much thought to how this would work with SSR, but looking around it seems one method would be to use the afterUpdate method. This allows the DOM to load before applying the className change.
