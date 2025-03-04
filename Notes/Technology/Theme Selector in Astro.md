# Theme Selector in Astro

The whole point (for me) of using Astro framework is to eliminate the need for other frameworks like React, Vue or Angular. We can write simple HTML, CSS and JS/TS and get a good looking static site. 

To make it more interesting, we need to add the option to toggle themes. As we purely want to use astro components, we can use scripts to change `data-theme` using `setAttribute` and `site-theme` using `setItem`.

Of course we need to select the theme. For that we have separate themeselector.

```js
// Theme selector logic
const themeSelector = document.getElementById("theme-selector");

// Event delegation for theme selection
themeSelector?.addEventListener("click", (event) => {
    const themeButton = (event.target as HTMLElement).closest(".theme-option");
    if (themeButton) {
        const selectedTheme = themeButton.getAttribute("data-theme");
        if (selectedTheme) {
            applyTheme(selectedTheme);
        }
    }
});
```

Of course, we need to have initial theme. So, it will look into the `localStorage` for `site-theme`, otherwise it will pick `light` as default.

```js
  // Initial theme application
  const currentTheme = localStorage.getItem("site-theme") || "light";
  applyTheme(currentTheme);
```

### Button Variant

```astro
---
// src/components/ThemeSelectorButton.astro

const themes = [
  { name: 'light', label: 'Light' },
  { name: 'dark', label: 'Dark' },
  { name: 'dracula', label: 'Dracula' },
  { name: 'nord', label: 'Nord' }
];
---

<div id="theme-selector-buttons">
  {themes.map((theme) => (
    <button 
      class="theme-option" 
      data-theme={theme.name}
      aria-label={`Select ${theme.label} theme`}
    >
      {theme.label}
    </button>
  ))}
</div>

<script>
  const buttonContainer = document.getElementById('theme-selector-buttons');
  
  const applyTheme = (theme: string) => {
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('site-theme', theme);
    
    // Update active state for buttons
    const buttons = document.querySelectorAll('.theme-option');
    buttons.forEach(btn => {
      btn.classList.toggle('active', btn.getAttribute('data-theme') === theme);
    });
  };

  buttonContainer.addEventListener('click', (event) => {
    const themeButton = (event.target as HTMLElement).closest('.theme-option');
    if (themeButton) {
      const selectedTheme = themeButton.getAttribute('data-theme');
      if (selectedTheme) {
        applyTheme(selectedTheme);
      }
    }
  });

  // Initial theme application
  const currentTheme = localStorage.getItem('site-theme') || 'light';
  applyTheme(currentTheme);
</script>

<style>
  #theme-selector-buttons {
    display: flex;
    gap: 0.5rem;
  }

  .theme-option {
    padding: 0.5rem 1rem;
    border: 1px solid var(--accent-color);
    background-color: transparent;
    cursor: pointer;
  }

  .theme-option.active {
    background-color: var(--accent-color);
    color: var(--bg-primary);
  }
</style>
```

### Dropdown Variant

```astro
---
// src/components/ThemeSelectorDropdown.astro

const themes = [
  { name: 'light', label: 'Light' },
  { name: 'dark', label: 'Dark' },
  { name: 'dracula', label: 'Dracula' },
  { name: 'nord', label: 'Nord' }
];
---

<select id="theme-selector-dropdown" aria-label="Select Theme">
  {themes.map((theme) => (
    <option value={theme.name}>
      {theme.label} Theme
    </option>
  ))}
</select>

<script>
  const dropdown = document.getElementById('theme-selector-dropdown') as HTMLSelectElement;
  
  const applyTheme = (theme: string) => {
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('site-theme', theme);
    dropdown.value = theme;
  };

  dropdown.addEventListener('change', (event) => {
    const selectedTheme = (event.target as HTMLSelectElement).value;
    applyTheme(selectedTheme);
  });

  // Initial theme application
  const currentTheme = localStorage.getItem('site-theme') || 'light';
  applyTheme(currentTheme);
</script>

<style>
  #theme-selector-dropdown {
    padding: 0.5rem;
    margin: 0.5rem 0;
    background-color: var(--bg-secondary);
    color: var(--text-primary);
    border: 1px solid var(--accent-color);
    border-radius: 4px;
  }
</style>
```

### Radio Button Variant

```astro
---
// src/components/ThemeSelectorRadio.astro

const themes = [
  { name: 'light', label: 'Light' },
  { name: 'dark', label: 'Dark' },
  { name: 'dracula', label: 'Dracula' },
  { name: 'nord', label: 'Nord' }
];
---

<div id="theme-selector-radio">
  {themes.map((theme, index) => (
    <label class="theme-radio-label">
      <input 
        type="radio" 
        name="theme" 
        value={theme.name} 
        checked={index === 0}
        aria-label={`${theme.label} theme`}
      />
      {theme.label}
    </label>
  ))}
</div>

<script>
  const radioInputs = document.querySelectorAll('input[name="theme"]');
  
  const applyTheme = (theme: string) => {
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('site-theme', theme);
    
    // Update radio button selection
    radioInputs.forEach(input => {
      (input as HTMLInputElement).checked = input.getAttribute('value') === theme;
    });
  };

  radioInputs.forEach(input => {
    input.addEventListener('change', (event) => {
      const selectedTheme = (event.target as HTMLInputElement).value;
      applyTheme(selectedTheme);
    });
  });

  // Initial theme application
  const currentTheme = localStorage.getItem('site-theme') || 'light';
  applyTheme(currentTheme);
</script>

<style>
  #theme-selector-radio {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  .theme-radio-label {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    cursor: pointer;
  }

  .theme-radio-label input {
    appearance: none;
    width: 20px;
    height: 20px;
    border: 2px solid var(--accent-color);
    border-radius: 50%;
    outline: none;
    cursor: pointer;
    position: relative;
  }

  .theme-radio-label input:checked::before {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 10px;
    height: 10px;
    background-color: var(--accent-color);
    border-radius: 50%;
  }
</style>
```

### Switch Variant

```astro
---
// src/components/ThemeSelectorSwitch.astro

const themes = [
  { name: 'light', label: 'Light' },
  { name: 'dark', label: 'Dark' }
];
---

<div id="theme-selector-switch">
  {themes.map((theme, index) => (
    <label class="theme-switch">
      <input 
        type="radio" 
        name="theme" 
        value={theme.name} 
        checked={index === 0}
        aria-label={`${theme.label} theme`}
      />
      <span class="slider"></span>
      {theme.label}
    </label>
  ))}
</div>

<script>
  const switchInputs = document.querySelectorAll('input[name="theme"]');
  
  const applyTheme = (theme: string) => {
    document.documentElement.setAttribute('data-theme', theme);
    localStorage.setItem('site-theme', theme);
    
    // Update switch selection
    switchInputs.forEach(input => {
      (input as HTMLInputElement).checked = input.getAttribute('value') === theme;
    });
  };

  switchInputs.forEach(input => {
    input.addEventListener('change', (event) => {
      const selectedTheme = (event.target as HTMLInputElement).value;
      applyTheme(selectedTheme);
    });
  });

  // Initial theme application
  const currentTheme = localStorage.getItem('site-theme') || 'light';
  applyTheme(currentTheme);
</script>

<style>
  #theme-selector-switch {
    display: flex;
    gap: 1rem;
    align-items: center;
  }

  .theme-switch {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    cursor: pointer;
    position: relative;
  }

  .theme-switch input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
  }

  .slider {
    display: inline-block;
    width: 40px;
    height: 20px;
    background-color: var(--accent-color);
    border-radius: 20px;
    position: relative;
    transition: background-color 0.3s;
  }

  .slider::before {
    content: '';
    position: absolute;
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background-color: white;
    top: 2px;
    left: 2px;
    transition: transform 0.3s;
  }

  .theme-switch input:checked + .slider::before {
    transform: translateX(20px);
  }
</style>
```
