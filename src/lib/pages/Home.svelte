<script>
    import logoCars from "../../assets/pictures/logoCars.svg"
</script>

<section class="presentation">
    <div>
        <h1>Amaury Madani, expert automobile</h1>
        <p>Fort de plusieurs années d’expérience, je met mon savoir-faire au service des automobilistes avec une approche à la fois humaine et professionnelle. Passionné par l’automobile et animé par une volonté d’offrir un accompagnement personnalisé, je m’engage à analyser chaque situation avec rigueur et transparence. Grâce à une expertise technique pointue, il intervient dans des domaines variés tels que les litiges, les évaluations de dommages ou encore les conseils pour l’achat et la vente de véhicules. Attentif aux besoins de ses clients, Amaury Madani privilégie toujours un dialogue clair et constructif, afin d’apporter des solutions adaptées et de garantir leur satisfaction. Confier votre véhicule à Amaury Madani, c’est faire le choix d’un expert à l’écoute, pour qui chaque détail compte.</p>
    </div>
    <div>
        <h2>Nos Valeurs</h2>
        <ul>
            <li>Impartialité</li>
            <li>Intégrité</li>
            <li>indépendance</li>
            <li>Excellence</li>
        </ul>
    </div>
</section>
<section class="services">
    <h2>Nos Services</h2>
    <ul>
        <li>Partenariat juridique</li>
        <li>Blablabla</li>
        <li>Blablabla2</li>
        <li>...</li>
    </ul>
    <ul>
        <li>Devis</li>
        <li>Evaluation des dommages</li>
        <li>Vices cachés</li>
        <li>Soupçons de fraude</li>
    </ul>
</section>

<section class="logoVehicules">
    <img src={logoCars} alt="Voiture citadine">
</section>

<section class="faq">
    <h2>FAQ</h2>
    <div class="accordeon">
        <p aria-hidden="true">↓</p>
        <h4>Dans quel contexte faire appel à un expert automobile ?</h4>
        <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
    </div>
    <div class="accordeon">
        <p aria-hidden="true">↓</p>
        <h4>Dans quel contexte faire appel à un expert automobile ?</h4>
        <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
    </div>
    <div class="accordeon">
        <p aria-hidden="true">↓</p>
        <h4>Dans quel contexte faire appel à un expert automobile ?</h4>
        <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
    </div>
</section>

<section class="formulaire">
    <h2>Formulaire de contact</h2>
    <form action="" method="post">
        <label for="demande">Quel est votre demande ?</label>
        <select name="demande" id="demande" required>
            <option value="information">Je souhaite avoir une information</option>
            <option value="Expertise">Expertise véhicule</option>
            <option value="autre">Autre</option>
        </select>

        <label>Est-elle urgente ?</label>
        <input type="radio" name="urgence" id="oui" value="oui">
        <label for="oui">Oui</label>
        <input type="radio" name="urgence" id="non" value="non">
        <label for="non">Non</label>

        <label for="location">Localisation de votre besoin ?</label>
        <select name="localisation" id="localisation" required>
            <option value="Montpellier">Montpellier</option>
            <option value="Bouches-du-Rhône">Bouches-du-Rhône</option>
            <option value="Var">Var</option>
            <option value="Gard">Gard</option>
            <option value="Hérault">Hérault</option>
        </select>

        <label for="nom">Votre nom</label>
        <input type="text" name="nom" id="nom" required>

        <label for="tel">Votre numéro de téléphone</label>
        <input type="tel" pattern="^0[1-9]( [0-9]{2}){4}$" placeholder="01.02.03.04.05" name="tel" id="tel">

        <label for="email">Votre e-mail</label>
        <input type="email" name="email" id="email" placeholder="example@gmail.com">

        <label for="commentaire">Un commentaire</label>
        <textarea name="commentaire" id="commentaire" required></textarea>

        <buttton type="submit">Envoyer</buttton>
    </form>
</section>