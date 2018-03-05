# polymer-cheatsheet

## polymer element template
```
<link rel="import" href="../bower_components/polymer/polymer-element.html">

<dom-module id="my-element">
  <template>
    <style>
      :host {
        display: block;
      }
    </style>
    <div>my element</div>
  </template>

  <script>
    class MyElement extends Polymer.Element {
      static get is() { return "my-element"; }
      static get properties() {
        return {
          isDebugging: {
            type: Boolean,
            value: true
          }
        }
      }

      connectedCallback() {
        super.connectedCallback();
        this.debug("connectedCallback", ":)");
      }

      debug(whoami, msg) {
        if (this.isDebugging) {
          console.log(MyElement.is + "." + whoami + ": ", msg || ":)");
          this.logState(whoami);
        }
      }

      logState(whoami) {
        let state = {
          isDebugging: this.isDebugging
        };
        console.log(MyElement.is + "." + whoami + " state: ", state);
      }
    }

    customElements.define(MyElement.is, MyElement);
  </script>
</dom-module>
```