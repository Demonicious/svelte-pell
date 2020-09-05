![svelte-pell](https://i.imgur.com/aS1a1Sw.png)

### Svelte-Pell
An implementation of [Pell](https://github.com/jaredreich/pell) as a Svelte Component.

#### 1. Installation
From [npm](https://npmjs.com/package/svelte-pell):
```
npm i -D svelte-pell
```

#### 2. Basic Usage
```html
<script>
    import PellEditor from "svelte-pell";

    let html = '';
</script>

<PellEditor bind:html={html} />
```
#### 3. Configuration
```html
// Refer to https://github.com/jaredreich/pell for all configuration options.
<script>
    import PellEditor from "svelte-pell";
</script>

<PellEditor 
    defaultParagraphSeparator="div"
    styleWithCSS={false}
    actions={[
        'bold',
        'underline',
        'strikethrough'
    ]}
    classes={{
        actionbar: 'pell-actionbar',
        button: 'pell-button',
        content: 'pell-content',
        selected: 'pell-button-selected'
    }}

/>
```
#### 4. Binding to Change Event
This is most likely-unnecessary since you can use `bind:html` Instead but:
```html
<script>
    import PellEditor from "svelte-pell";

    function changeHandler(e) {
        const { html } = e.detail;

        console.log(html);
    }
</script>

<PellEditor on:change={ changeHandler } />
```
