<script>
    import {link} from "svelte-spa-router"
    import logoLinkedIn from "../../assets/pictures/logoLinkedin.svg"
    import logoIeta from "../../assets/pictures/logoIeta.png"
</script>

<footer>
    <a href="/legalNotices" use:link aria-label="Aller à la page mention légales">Mention légales</a>
    <img src={logoIeta} alt="Logo I.E.T.A : Innovation, expertise des technologies automobiles">
    <a><img src={logoLinkedIn} alt="Lien pour aller sur le profil LinkedIn d'Amaury Madani"></a>
</footer>

<style lang="scss">
    footer {
        background-color: var(--backgroundComponents);
        background: linear-gradient(135deg, #2b2b3d, #41415c);  
    }
</style>