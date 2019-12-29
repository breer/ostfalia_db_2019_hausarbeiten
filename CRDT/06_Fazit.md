# Fazit

Moderne PA-Datenbanksysteme mit "Eventual Consistency" müssen zwangsläufig mit Konflikten umgehen. Die in diesem Beitrag vorgestellten Conflict-Free Replicated Data Types (CRDTs) lösen dieses Problem auf einem abstrakten Niveau. Somit muss die Konfliktlösungsstrategie nicht vom Anwendungsentwickler implementiert werden. CRDTs können, wie am Beispiel von Automerge zu sehen, sowohl als Softwarebibliothek, also auch im Fall von Riak direkt in der Datenbank umgesetzt werden. Durch die Nutzung von CRDTs konvergieren die Daten automatisch auf allen Replikaten und die Komplexität der Konfliktbehandlung wird gekapselt. Ein Anwendungsentwickler sieht bei einem CRDT nur die gewohnte Schnittstelle des synchronen Pendant des Datentyps.

Ein häufig angeführtes Argument für die anwendungsseitige Konfliktlösung ist, dass für die Konfliktbehandlung Domänenwissen erforderlich sei und somit die Konfliktlösungsstrategie ein Teil der Anwendung sein sollte. Es ist nicht von der Hand zu weisen, dass die beste Art des Konfliktbewältigung vom Anwendungsfall abhängt. Soll bei einen Warenkorb für eine E-Commerce-Anwendung im Fall eines Konfliktes der gelöschte oder der soeben hinzugefügte Eintrag den Vorzug erhalten? Im Fall eines Sets existieren für beide Strategien unterschiedliche CRDTs. Während bei einem 2P-Set im Konfliktfall die Löschen-Operation favorisiert wird, bleibt beim, im Kapitel 4 vorgestellten OR-Set das hinzufügte Element erhalten. So muss sich der Anwendungsentwickler auch bei der Nutzung von CRDTs über die Funktionsweise der Merge-Funktion bewusst sein. Sonst kann der Einsatz von CRDTs gerade in Ausnahmefällen zu ungewünschten Ergebnissen führen.