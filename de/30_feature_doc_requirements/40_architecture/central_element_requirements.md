#### Zentrales Element Requirements (2.)
Requirements sind das zentrale Element im System Scope. Fast alle Elemente referenzieren diese einzelnen Anforderungen. Das möglichst so, dass die beschriebenen Arten von Änderungen jeweils nur an einer Stelle eine Veränderung der Dokumentation verursachen.
Die System-Vision ist die einzige Ausnahme – ich gehe davon aus, dass eine System-Vision hinreichend stabil ist, um referenziert zu werden.
Damit die Gratwanderung zur Übersicht über das System gelingt, werden Anforderungen auf einer möglichst hohen Abstraktionsebene beschrieben.
Anforderungen haben die folgenden Eigenschaften:
* Sie sind eindeutig identifizierbar und referenzierbar (wird durch den Stereotyp <<entity>> gekennzeichnet).
* Sie sind einzeln versioniert (wird durch den Stereotyp <<versionable>> gekennzeichnet). Als versionierbare Objekte sind Anforderungen implizit auch veränderbar. Veränderungsdatum und Autor werden festgehalten.
* title: Neben der ID haben Anforderungen auch einen Titel. Erfahrungsgemäß verändert sich der Titel des öfteren und wird daher nicht zur Referenzierung verwendet.
* state: In unserem Fall reicht die einfach Unterscheidung in [premature, mature, deprecated].
* Optional kann auf Ebene von Anforderungen zusätzlich der Geschäfts-Wert erfasst werden. Diese Größe ist für eine Kosten unabhängige Priorisierung von Anforderungen nützlich.
Die folgenden Anforderungstypen werden typischerweise unterschieden: