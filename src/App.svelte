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

    // kebab-case plus naturel pour le SEO
    const routes = {
        "/": Home,
        "/legal-notices": LegalNotices,
        "*": NotFound,
    };

    const onRouteLoaded = () => {
        // Forcer le scroll en haut de la page
        window.scrollTo(0, 0);

        // requestAnimationFrame plus fluide que le setTimeout
        requestAnimationFrame(() => {
            // Vérifier si l'URL contient une ancre, et si oui, faire défiler
            const hash = window.location.hash.replace("#", ""); // Enlève le #
            if (hash) {
                const target = document.querySelector(hash);
                if (target) {
                    target.scrollIntoView({ behavior: "smooth" });
                }
            }
        });
    };

    // Empêcher le navigateur de restaurer la position de scroll automatiquement
    if ('scrollRestoration' in history) {
        history.scrollRestoration = 'manual';
    }
</script>

<Header />
<Router {routes} on:routeLoaded={onRouteLoaded} />
<Footer />