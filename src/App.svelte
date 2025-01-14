<script>
    // Importer le router
    import Router from 'svelte-spa-router'

    // Importer les composants
    import Header from './lib/components/Header.svelte'
    import Footer from './lib/components/Footer.svelte'

    // Importer nos pages
    import Home from "./lib/pages/Home.svelte";
    import LegalNotices from "./lib/pages/LegalNotices.svelte";
    import NotFound from "./lib/pages/NotFound.svelte";

    const routes = {
        "/": Home,
        "/legalNotices": LegalNotices,
        "*": NotFound,
    }
</script>

<Header />
<Router {routes} />
<Footer />