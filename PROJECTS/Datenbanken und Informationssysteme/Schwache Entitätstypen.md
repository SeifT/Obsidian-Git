**A weak entity is an entity that cannot be uniquely identified by its own attributes alone and depends on a related strong entity for its identification and existence.**

Ohne Hörsaalgebäude kann es keine Seminarräume geben.

![[Pasted image 20250521130116.png]]
Here, the entity "Seminarraum" and the relation "liegt in" are weak. This means that Seminarraum's existence depends on another entity, i.e. Hörsaalgebäude. 
BA: Any attributes of Seminarraum are not globally unique. They are unique only under Hörsaalgebäude and therefore when trying to identify a Seminarraum, you need both the Hörsaalgebäude it belongs to *and* its RaumNr.

