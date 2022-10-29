# Sveltekit dark mode example

A simple example of switching between light and dark modes using Sveltekit. This example should:

- Use OS/browser preference
- Allow overriding native setting
- Store preference in local storage

You can see in the **themes.css** file within the static folder there is a themes.css file which has two classes. At the moment these are swapped within **+layout.svelte** in the src folder, setting the body tag's class to get either light or dark. The issues with this is that we often want to set more than just the body style for different modes. Some possible solutions to this setting it up to add more css selectors or instead swapping out css files within **svelte:head**. 


