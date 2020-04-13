<script>
    export let to;
    export let attributes;
    let url = window.location.origin.replace(/^\/|\/$/g, '') + '/#/' + to.replace(/^\/|\/$/g, '');
</script>

<a href={url} {...attributes}><slot></slot></a>