<script lang="ts">
	import { onMount } from 'svelte';
	let isDarkmode: boolean;

	/**
	 * Takes the class name of the theme as given in the themes.css file
	 *
	 * The function sets the class on the body to the correct theme. If you have
	 * classes already defined then you could use the classList element to add/remove
	 * themes as need be without affecting existing classes.
	 *
	 * Here we also set a "site-theme" key to the name of our string. Best to change
	 * the 'site-theme' to better suit your site. Lastly, we set isDarkmode based on
	 * if the theme is dark or not. If you have more themes than light/dark, then
	 * you'll want to rework this.
	 *
	 */
	function setTheme(theme: string) {
		document.body.className = theme;
		localStorage.setItem('site-theme', theme);
		isDarkmode = theme === 'dark' ? true : false;
	}

	/**
	 * Used whenever selecting the theme. Only works for two themes (see comment
	 * in the setTheme function).
	 */
	function toggleTheme() {
		setTheme(isDarkmode ? 'light' : 'dark');
	}

	/**
	 * Sets user preferences based on system preferences.
	 *
	 * If the user has dark mode set on their browser it will default to that mode,
	 * but only if the user doesn't already have a preferred mode saved in local
	 * storage.
	 */
	onMount(() => {
		let theme: string | null = localStorage.getItem('site-theme');
		let prefersDarkmode = window.matchMedia('(prefers-color-scheme: dark)');
		if (!theme && prefersDarkmode.matches) {
			setTheme('dark');
		} else {
			setTheme('light');
		}
	});
</script>

<label>
	<input type="checkbox" bind:checked={isDarkmode} on:click={toggleTheme} />
	Toggle light/dark
</label>
