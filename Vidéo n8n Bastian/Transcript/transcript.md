# Transcript de la vidéo de présentation du workflow n8n

Transcription fournie par Bastian, conservée avec ses horodatages et sans correction du texte.

**0:01** Hello Lucas, j'espère que tu vas bien. Je suis, Déjà je commence pour, Je m'excuse parce que je fais cette vidéo le lundi, j'ai passé un week-end pas ouf, j'étais hyper malade, je vais la faire ce week-end la vidéo, mais vraiment j'avais plus de voix, enfin j'avais mal à la gorge, etc, Donc là j'espère

**0:16** que ça va mieux. J'espère que tu vas bien m'entendre et que ça va aller pour la vidéo, mais en tout cas voilà, d Donc je tenais à m'excuser pour ça, pour le désagrément.

**0:30** Donc tout d'abord, je vais te présenter le GitHub, là où j'ai mis les trois skills que tu avais demandé, donc sous format MD, Markdown.

**0:41** Et là, tu as le fichier de la vidéo que je suis en train de réaliser. Ensuite, tu auras, Enfin, j'ai déjà fait j déjà mis le workflow format ts voilà donc normalement tout est good il réajuste la vidéo qu'on est en train de faire maintenant voilà donc mon workflow je vais le déplier pour que ça soit

**1:02** un peu plus clair voilà donc mon workflow il sert à quoi ? c'est quoi l'idée ? c'est quoi le projet derrière ce workflow ?

**1:12** c'est que tout simplement je suis quelqu'un qui malheureusement oublie beaucoup les anniversaires de mes proches. Voilà, donc pas top. Et même si je mets un rappel sur mon calendar Apple, voilà, même si j'ai la notif, à un moment je vais me dire je vais le faire après et puis en fait je le fais jamais

**1:32** . Enfin j'oublie et puis c'est souvent le lendemain je me dis oh non j'ai oublié l'anniversaire tout ça. Donc là, j'ai eu cette solution grâce à ce workflow, je me dis, là, plus aucune excuse, je vais recevoir un mail avec un message préfet sur la relation que j'ai avec la personne.

**1:47** Donc là, vraiment, je n'ai plus aucune excuse. Tout simplement, dans un Google Sheet, donc là, tac, je vais décaler ma tête, j'ai papa, maman, Emma.

**2:00** Donc, relation que j'ai famille-famille et ma copine. Voilà, donc j'ai renseigné la date d'anniversaire pour que le workflow puisse lire ce cheat assez clairement.

**2:15** Donc, première étape de mon workflow, c'est un test. il va juste lire mon cheat et on reviendra. dire ouais nickel tout est bien rempli.

**2:28** Donc ça je peux l'exécuter à tout moment. Voilà nickel. Ensuite deuxième étape, j'ai un trigger tous les matins à 9h qui se déclenche, donc mon workflow se déclenche tous les matins à 9h, heure de Paris, donc pour voir s'il y a donc des anniversaires etc.

**2:48** Donc ça c'est la partie pour ne pas qu'il fasse de bêtises, pour ne pas qu'il m'envoie des doublons, pour ne pas qu'il me fasse des trucs bizarres s'il y a deux anniversaires dans la même journée, etc.

**2:59** Et ça c'est la dernière partie, donc la partie la partie principale où il y a la création du message. Enfin déjà d'abord il lit, donc mon guillotine, tiens l'anniversaire, il me fait un message selon la relation.

**3:13** Donc voilà, vu que j'ai bien écouté les cours, j'ai bien mis Gimini, Flash, Lite, la test, donc la test pour avoir toujours la dernière version, et ensuite donc le prompt.

**3:24** Donc en fonction de la relation, voilà, ce sera un message chaleureux et affectueux, si c un ami proche, si c'est un ami, si c un collègue, voilà, j'ai mis toutes les, comment dire, les relations possibles que je pouvais avoir.

**3:39** et ensuite donc lui il va me m'envoyer un mail et comme ça je l'ai directement dans la boîte mail donc là par exemple j'ai fait un test tout à l'heure où ça fait donc anniversaire papa donc là aujourd'hui c'est l'anniversaire de papa voilà comme ça j'ai pas loupé et ensuite donc mes !

**4:01** Il ne va pas me donner toujours le message 100% accurate de ce que je veux lui envoyer, mais au moins il me le fait et j'ai juste à le prendre, à le copier, à le coller et à modifier ce que j'ai envie.

**4:15** C'est pour ça que là, je n'ai plus d'excuses. Ensuite, qu'est-ce que j'avais à présenter ? Voilà, je t'ai présenté donc mon workflow.

**4:25** pourquoi celui-là et pas un autre, ensuite voilà, les commandes, les fameuses commandes. Donc voilà, j'ai déjà préparé les commandes que je vais présenter.

**4:35** Donc la première c'est la commande classique "--help". Donc ça va me recenser toutes les commandes que je peux faire avec la commande.

**4:49** la connexion N-Utensil, tout ce que je peux faire avec, ensuite je vais te montrer la commande version, donc pour te montrer la version dans laquelle j'étais, donc la 1.2.45, donc la dernière qu'on avait qu'on avait eu en cours, que tu nous avais dit de mettre à jour, et ensuite la changelog, C'est la

**5:14** commande qui nous sert à voir ce qui a été mis à jour via les dernières versions et notamment la dernière que tu nous as faite qui est la 1.2.45 où tu nous as rectifié certains bugs, certaines nouveautés, etc.

**5:37** donc ça rend le CLI plus propre. Ensuite, qu'est-ce qu'on avait d'autre à faire ? Je t'ai montré, je t'ai exécuté le workflow ici, je peux aussi l'exécuter ici.

**6:01** Ici, pour voir, Bon là, vu qu'il n pas d'anniversaire, voilà, ça le met en bas. Et puis, ah oui, le feedback.

**6:09** Feedback. Alors, c'est un point personnel, je trouve qu'on était trop dans la classe. Enfin, du moins, on est quand même plus de 40 sur la semaine.

**6:22** On était, ouais, une quarantaine de personnes et je trouve que que c'est un peu dur, sachant que moi c'était une notion que je ne connaissais pas du tout à 8N, donc je ne me voyais pas t'interrompre toutes les 5 minutes et te dire « ouais, est-ce que tu peux plus expliquer ça ?

**6:37** Est-ce que tu peux aller davantage vers ce sujet ? Est-ce que tu peux vraiment revenir sur ça et expliquer en détail ?

**6:44** » Enfin, ce n'est pas possible quand on est plus de 40 dans une classe, et j'en suis bien conscient, et ce n'est pas du tout de ta faute.

**6:50** Donc voilà, heureusement qu'il y avait quand même des camarades qui sont bienveillants et que je pouvais, comment dire, leur poser des questions, etc.

**6:59** Mais sinon, sur ton cours en particulier, moi j'ai apprécié cette semaine, découvrir Ann Witten, c'était hyper important, et surtout toi, parce que, franchement, en tant que personne c'était hyper cool de t'avoir et je ne suis pas resté à toutes les à toutes les masterclass, mais en tout cas c'était

**7:17** un plaisir de t'avoir comme prof pendant une semaine. Donc qu'est ce que j'avais d'autre à dire ? Que non, j'ai pris du plaisir à construire ce workflow, donc non franchement, c'est ce qui va m'être utile.

**7:37** Pour l'instant, oui, il me reste deux jours de test. Est-ce que je vais prendre un abonnement ? Je ne sais pas encore.

**7:44** Mais en tout cas, j'ai vraiment pris du plaisir à construire ce workflow. C'est un peu comme un jeu. En fait, c'est devenu comme un jeu, même si je me suis beaucoup aidé de l'IA, notamment quand on l'a connecté avec Tchat.

**8:00** Mais franchement, ça a été un rêve. plaisir donc je te remercie je te remercie pour cette semaine et tout notamment pour le petit goûter j'ai vraiment apprécié le moment d'échange etc qu'on a eu qu'on a eu ensemble puis voilà donc merci beaucoup j'arrête la vidéo ciao
