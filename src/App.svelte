<script>
    // Importer le router
    import Router from 'svelte-spa-router'

    // Importer les composants
    import Header from './lib/components/Header.svelte'
    import Footer from './lib/components/Footer.svelte'

    // Importer nos pages
    import Home from "./lib/pages/Home.svelte";
    import NotFound from "./lib/pages/NotFound.svelte";

    const routes = {
        "/": Home,
        "*": NotFound,
    }
</script>

<Header />
<Router {routes} />
<Footer />