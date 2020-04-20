Mono-repo mono-branch
---------------------

My expérience:
* 2013 &emsp; Architech of three software teams (for a big bank), migrating CVS code to Git repo(s), I was wondering about [one repo for different teams](https://softwareengineering.stackexchange.com/questions/206668/)
* 2015 &emsp; Being the first consultant designing the rewrite of a new matching engine (for a big stock exchange), organizing source code and teams, adopting Agile mindset and many other transformations (coding/commit rules, CI/CD, branching model, dependency/release management, DoD...)

Constraints and learning:

* Le meta projet de l'entreprise a besoin d'être découpé en micro-projets gérables par de petites équipes
* Chaque équipe à des dépendances avec les autres => il faut donc chercher à inciter la collaboration entre les équipes
* Devoir synchroniser les versions de plusieurs repo de code source est source d'erreur, de frustration => Ne pas perdre de temps avec cette tâche
* Ce n'était pas une bonne idée les submodules, trop compliqué pour la majorité des développeurs => On passait trop de temps à régler les mauvaises manips
* On avait un super branching model où chaque équipe avait apporté sa pierre à l'édifice => Au final, on n'y voyait pas clair, et des branches étaient oubliées

After many years practitioning different use cases, my position is Simplicity:

* Tout le monde ne connaît pas Git sur le bout des doigts => Faire au plus simple
* Pour suivre ce que font les autres équipes => avoir leur code source dans le même repo
* Le moins de branches possibles => Pourquoi pas avoir toutes les équipes sur la branche principale, branches possibles si nécessaire, éviter les branches qui s'éternisent
* Les commit rules et Git hooks => Ça frustre le dév qui comprend pas pourquoi tel fichier est refusé
* Offrir plutôt des outils (scripts du Git hook) pour vérifier ses changements avant le commit et faire confiance dans la bonne volonté des dév
* Les messages de commit n'ont plus trop d'intérêt après quelques mois => Pas besoin d'investir du temps à découper ses commits (`git add -p`) sauf si c'est justifié
* On responsabilise le développeur, et on blinde le CI pour détecter les erreurs
* Frustration des codeurs à devoir rédiger des documents sous MS-Office, connaître l'organisation des répertoires partagés... => Markdown => Frustration des managers car ne connaissent pas GitLab => Générer la doc à partir du MD => Site web => Mettre des liens "Edit this document"

Bien sûr, pour des livraisons sans dépendance, le multi-repo est parfait.


Configuration
-------------

* [`~/.gitconfig`](./configuration.md)


Commit
------

Nice example: https://github.com/tiangolo/fastapi

:memo: Update release notes  
:sparkles: Add support for OpenAPI Callbacks (#722)  
:loud_sound: Refactor logging (#781)  
:speech_balloon: Rephrase handling-errors to remove gender

Useful emojis: https://github.com/carloscuesta/gitmoji

Elegant commit message:

    :emoji: Verb summarizing the change (in some words) #123 #456 (optionnal issues)
                                                                      (blank line)
    Optionnal verbose descripption
    can use multiple lines
    * can use bullet points
    * and any *Markdown* `syntax`

* But we not care about perfect commit history
* We care about the current source code status (not about what we did last year)
* Each one is free to commit in the way they want (even poor commit message *"WIP"* if team members do not care)
* Each one is free to `git push --force` on their own feature branch
* But inform others when you `git push --force` on `master` 🙏



Branching
---------

* Simplicity: no unnecessary branches
* Only `master` and temporary feature branches (we may add `develop` and others in the future)
* Delete old branches
* Feature branch is nice for:
    * risk of regression
    * merge request (you want someone review your changes)
* But new code (new subdirectory) can be commited *in progress* in the `master` branch (if others do not care)
* And if the change is obvious (one commit) you can also do it in `master` branch (review is easy for one commit)
* Anyone is free to break these rules: Liberty and happiness is more important than constraints

See also:

* [branch](./branch.md)
* https://learngitbranching.js.org/
