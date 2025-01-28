<script>
    import {link} from "svelte-spa-router"
    import logoLinkedIn from "../../assets/pictures/logoLinkedin.svg"
    import logoIeta from "../../assets/pictures/logoIeta.png"
    import { onMount } from 'svelte';

  // Forcer le défilement après chaque navigation
    onMount(() => {
        const handleScroll = () => {
        window.scrollTo(0, 0);
    };

    // Écoute les changements d'URL (navigations)
    window.addEventListener('sveltekit:navigation-end', handleScroll);

    return () => {
      // Nettoyage à la destruction du composant
        window.removeEventListener('sveltekit:navigation-end', handleScroll);
    };
    });
</script>

<footer>
    <a href="/legalNotices" use:link aria-label="Aller à la page mention légales" class="legalNotices">Mention légales</a>
    <a href="#home" aria-label="Retour à l'accueil"><img src={logoIeta} class="logoIeta" alt="Logo IETA : Innovation, expertise des technologies automobiles"></a>
    <a href="https://www.linkedin.com/in/amaury-m-5638a1192/" use:link aria-label="Ouverture d'une nouvelle page du profil LinkedIn d'Amaury Madani" target="_blank"><img src={logoLinkedIn} class="logoLinkedIn" alt="Lien pour aller sur le profil LinkedIn d'Amaury Madani"></a>
</footer>

<style lang="scss">
    footer {
        background-color: var(--backgroundComponents);
        background: linear-gradient(135deg, #2b2b3d, #41415c); 
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0 1rem;


        .legalNotices {
            color: white;
            font-size: 0.7rem;

            @media (min-width: 768px) { // Tablette
                font-size: 0.9rem;
            }

            @media (min-width: 1024px) { // Laptop
                font-size: 1rem;
            }
        }

        .logoIeta {
            width: 5rem;

            @media (min-width: 768px) { // Tablette
                width: 6rem;
            }

            @media (min-width: 1024px) { // Laptop
                width: 6.5rem;
            }
        }

        .logoLinkedIn {
            width: 1.8rem;
            margin-right: 0.5rem;

            @media (min-width: 768px) { // Tablette
                width: 2rem;
            }

            @media (min-width: 1024px) { // Laptop
                width: 2.5rem;
            }
        }
    }
</style>