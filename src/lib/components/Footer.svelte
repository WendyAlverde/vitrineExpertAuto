<script>
    import {link} from "svelte-spa-router"
    import logoLinkedIn from "../../assets/pictures/logoLinkedin.svg"
    import logoIeta from "../../assets/pictures/logoIeta.png"
</script>

<footer>
    <a href="/legalNotices" use:link aria-label="Aller à la page mention légales" class="legalNotices">Mention légales</a>
    <a href="/" use:link aria-label="Retour à l'accueil"><img src={logoIeta} class="logoIeta" alt="Logo IETA : Innovation, expertise des technologies automobiles"></a>
    <a href="https://www.linkedin.com/in/amaury-m-5638a1192/" use:link aria-label="Redirection vers le profil LinkedIn d'Amaury Madani"><img src={logoLinkedIn} class="logoLinkedIn" alt="Lien pour aller sur le profil LinkedIn d'Amaury Madani"></a>
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
        }

        .logoIeta {
            width: 5rem;
        }

        .logoLinkedIn {
            width: 1.8rem;
            margin-right: 0.5rem;
        }
    }
</style>