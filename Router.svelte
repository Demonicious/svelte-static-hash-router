<script>
    export let notfound;
    export let routes;
    let routecomponent = null, props = {};
    if(window.location.hash === '') window.location.hash = "#/";
    const determineRoute = () => {
        let url = window.location.hash.replace('#', '').replace(/^\/|\/$/g, '');
        let route_objects;
        if(url === '') {
            route_objects = routes.filter(r => (r.path === '' || r.path === '/'));
            if(route_objects.length > 0) {
                props = route_objects[0]['props'] ? route_objects[0]['props'] : {};
                routecomponent = route_objects[0]['component'];
            } else if(notfound) routecomponent = notfound;
        } else {
            route_objects = routes.filter(r => (r.path.replace(/^\/|\/$/g, '') === url));
            if(route_objects.length > 0) {
                props = route_objects[0]['props'] ? route_objects[0]['props'] : {};
                routecomponent = route_objects[0]['component'];
            } else if(notfound) routecomponent = notfound;
        }
        console.log(props);
    }
    window.addEventListener('hashchange', determineRoute);
    determineRoute();
</script>

{#if routecomponent}
    <svelte:component {...props} this={routecomponent} />
{/if}
