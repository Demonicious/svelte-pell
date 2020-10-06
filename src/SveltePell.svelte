<script>
    import { init } from "pell/src/pell.js";
    import { createEventDispatcher } from "svelte";

    export let html = '';
    export let defaultParagraphSeparator = 'div';
    export let styleWithCSS              = false;

    export let actions = [
        'bold',
        'italic',
        'underline',
        'strikethrough',
        'heading1',
        'heading2',
        'paragraph',
        'quote',
        'olist',
        'ulist',
        'code',
        'line',
        'link',
        'image'
    ];
    export let classes = {
        actionbar: 'pell-actionbar',
        button: 'pell-button',
        content: 'pell-content',
        selected: 'pell-button-selected'
    };

    const dispatch = createEventDispatcher();

    const editor = (node) => {
        init({
            element: node,
            onChange: (contents) => {
                html = contents;
                dispatch('change', {html: contents});
            },
            defaultParagraphSeparator,
            styleWithCSS,
            actions,
            classes,
        });
    }
</script>

<svelte:head>
    <link rel="stylesheet" href="https://unpkg.com/pell@1.0.6/dist/pell.min.css" id="pell-theme" />
</svelte:head>

<div use:editor id="svelte-pell-node" class="pell" />
