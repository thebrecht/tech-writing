# Drupal Relation Module

Relation 模組提供 API 和 基本的使用者介面，用來建立和處理實體(entity)之間的關聯，這個模組可以很好地處理雙向、對稱的關係。

https://www.drupal.org/project/relation

## 使用情境
- 可以在超過2個實體間建立關聯:
areSiblings -> (john, jen, jack, jess)

- 雙邊關聯可以是具備方向性的：
bruno -> isChildOf -> boglarka

- 具方向性的關係可以自動提供反向的關聯：
boglarka -> isParentOf -> bruno

- 也可以建立1:n 的方向關聯性:
john -> playlist -> (Song A, Song B, Song C)

- 關聯可以是欄位
CompanyA -> donation[123] -> PartyB, donation[123] 可以是數量、日期、訊息的欄位

- 以實體而言，關聯性可以再與其他關係作關聯:
CompanyA -> donation[123] -> PartyB 和 donations[123] -> transaction[456] -> BankC
這是的關係是Company A 捐款給政黨B, 透過銀行C

## 建立關聯類型

你的網站可能有許多不同的關聯型態，包含求同的資訊並且用在不同的目的上。這些都透過不同的關聯類型來處理，類似於你的網站擁有不同的文件類型。

###  建立關聯類型

要使用Relation模組，你至少要建立一個關聯類型。在 administration toolbar > Structure > Relation types，你可以看到可以使用的關聯類型，並有一個連結可以新增關聯類型。

建立關聯提供了下面的選項:

Label: This is the name of the relation. It is usually only displayed to administrators, but if using the natural language formatter for the Relation Dummy Field (see separate section), it will also be displayed to end users. If so, you should strive to have the label expressed as a predicate, such as "is sibling to" or "is creator of".
Machine name: A machine name is suggested based on the relation label, but can be edited manually too.
Directional: For directional relation types, Relation will treat the first referenced entity as the source and the other entities as targets. While this has some effects on how you set up your relation, and for example how it can be used with Views, it does not affect how the internal data of the relation. Your use case determines if your relation should be directional or not.
Reverse label: If you are setting up a directional relation, you will get a chance to set up a reverse label – used to indicate the reverse relation. For example, an "is creator of" relation could have the reverse label "was created by".
Available source bundles: This option specifies which types of entities can be included in the relation. All entity bundles available on your site are listed – such as specific content types and taxonomy terms divided by vocabularies. If you want to restrict on entity type only, and not by bundle, select "all [entity] bundles". You may select multiple entries, even from different entity types.
Available target bundles: If your relation is directional, the target bundles are set up separately from the source bundles.
Advanced options
Transitive: Relations that "pass on" its relatedness are called transitive relations. One example is "is sibling with", since if Alice is sibling with Bob and Bob is sibling with Eve, then the relation passes on the relatedness and Alice is sibling with Eve too. However, the Relation module does not provide nor use this extra relationship in any way – it is merely an information flag to be used by other modules.
Unique: If this option is checked, no relations with the same end points as an existing relation (of the same type) will be allowed.
Minimum arity: This defines the minimum number of end points for the relation. Currently it is only possible to select between 2/3/4/5/8 end points.
Maximum arity: This defines the maximum number of end points for the relation. Currently you have the same options as for minimum arity, plus infinite.
Adding fields and editing relation types

At the administration overview of relation types there are links for editing the properties for each relation type, as well as managing fields attached to each type (and how they are displayed). The edit screen for relation types is identical to the creation screen described above. Fields are managed in the same way as for other (fieldable) entities.

All relation entities have the endpoints field, provided by the (required) Relation Dummy Field module. The only available formatter for this field is the endpoints table, displaying a table of all the endpoints included in the viewed relation. There are no view modes defined for the Relation entity.


