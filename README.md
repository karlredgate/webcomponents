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

Constructors are bound by the following requirements:

 * A parameter-less call to `super()` must be the first statement
   in the constructor body, to establish the correct prototype chain
   and this value before any further code is run.

 * A return statement must not appear anywhere inside the constructor
   body, unless it is a simple early-return (return or return this).

 * The constructor must not use the `document.write()` or
   `document.open()` methods.

 * The element's attributes and children must not be inspected, as
   in the non-upgrade case none will be present, and relying on
   upgrades makes the element less usable.

 * The element must not gain any attributes or children, as this
   violates the expectations of consumers who use the `createElement`
   or `createElementNS` methods.

 * In general, work should be deferred to `connectedCallback` as
   much as possible—especially work involving fetching resources
   or rendering. However, note that `connectedCallback` can be
   called more than once, so any initialization work that is truly
   one-time will need a guard to prevent it from running twice.

 * In general, the `constructor` should be used to set up initial
   state and default values, and to set up event listeners and
   possibly a shadow root.


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

## Templates

 * <https://developer.mozilla.org/en-US/docs/Web/HTML/Element/template>

<!-- vim: set autoindent expandtab sw=4 syntax=markdown: -->
