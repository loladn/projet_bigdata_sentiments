# Projet : Analyse de Sentiment en Temps Réel sur Flux de Tweets

## Contexte du projet
Ce projet a été développé dans le cadre de ma troisième année de BUT Science des Données. Il s'agit de concevoir un système complet d'analyse de sentiment en temps réel appliqué à un flux de publications (tweets). L'outil agit comme une plateforme de veille stratégique qui surveille la réputation en ligne d'une marque en continu. Son but est de détecter les signaux faibles pour déclencher des alertes immédiates en cas de crise ou de "bad buzz".

## Processus de réalisation
L'architecture technique et le développement de ce pipeline Big Data se sont déroulés en quatre grandes étapes.

1. **Mise en place des indicateurs en streaming**
J'ai utilisé Spark Structured Streaming pour analyser les flux en temps réel. Cette première brique calcule des métriques dynamiques sur des fenêtres temporelles glissantes, permettant de suivre les volumes de publication, l'évolution de la popularité des hashtags et les ratios globaux de sentiment.

2. **Modélisation Machine Learning**
J'ai entraîné un modèle d'analyse de texte avec PySpark MLlib. Le processus de traitement du langage naturel comprend le nettoyage du texte brut, la tokénisation, l'extraction des caractéristiques via TF-IDF, puis une classification binaire par régression logistique servant à déterminer si le contenu est positif ou négatif.

3. **Déploiement du pipeline de production**
L'architecture temps réel a ensuite été assemblée. Les données sont ingérées via un producteur Kafka dans un topic dédié. Spark Streaming consomme ces messages, fait appel au modèle d'apprentissage automatique préalablement stocké sur HDFS pour réaliser l'inférence à la volée, et écrit les résultats continuellement.

4. **Visualisation et monitoring**
Le projet s'achève par le développement d'un tableau de bord analytique construit avec Pandas et Plotly. Il se met à jour en direct pour restituer la répartition des sentiments, suivre les pics de volume et remonter des alertes intelligentes basées sur des écarts statistiques.

## Finalité
Le résultat est un pipeline de bout en bout, allant de l'ingestion de la donnée brute jusqu'à sa restitution métier. Ce projet démontre l'orchestration de technologies distribuées (Kafka, Spark, HDFS) dans le but de transformer un flux massif de données non structurées en un outil d'aide à la décision réactif et visuel.
