Example Webcomponents
---------------------

Testing repo

```
class Widget extends HTMLElement {...}
window.customElements.define('custom-widget', Widget);
// OR
window.customElements.define('custom-widget', class extends HTMLElement {...});
```

## Rules

 1. The name of a custom element must contain a dash (-).
    This requirement is so that the HTML parser can distinguish
    custom elements from regular elements.
 2. You can't register the same tag more than once.
    Attempting to do so will throw a DOMException.
 3. Custom elements cannot be self-closing because HTML only allows
    a few elements to be self-closing.

## Reactions

### `constructor`

### `connectedCallback`

### `disconnectedCallback`

### `attributeChangedCallback(attrName, oldVal, newVal)`

## Methods

```
class Widget extends HTMLElement {
    get slotName() {
        return this.hasAttribute( 'slotName' );
    }
    set slotName( value ) {
        if ( value ) {
	    this.setAttribute( 'slotName', value );
	} else {
	    this.removeAttribute( 'slotName' );
	}
	this.toggleSetting();
    }
    constructor() {
        super();
	this.addEventListener( 'eventName',
	    event => {
	        if ( this.disabled ) return;
		this.toggleSetting();
	    }
	);
    }
    toggleSetting() {
    }
}
customElements.define( 'custom-widget', Widget );
```

<!-- vim: set autoindent expandtab sw=4 syntax=markdown: -->
