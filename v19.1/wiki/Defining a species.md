This page describes **how to define a Pokémon species**.

## Defining a species

A Pokémon species begins with its definition. This means that it is
listed in the [PBS file](PBS_file "wikilink") "pokemon.txt", so that it
can be recognised by the game as a species.

Note that this only defines the basic properties common to all
individual Pokémon of that species (e.g. base stats, move sets,
evolution paths, etc.).

In addition to this, a species will require a number of graphics files
depicting that species in different ways, as well as an audio file which
plays its cry. See below for more information.

## PBS file "pokemon.txt"

The [PBS file](PBS_file "wikilink") "pokemon.txt" lists all the defined
Pokémon species in the game. Each section in this file is one separate
species, where a section begins with a line containing an ID number in
square brackets and ends when the next section begins. Each line in a
section is one separate piece of information about that species.

Aside from the ID line, every line in a section follows the format:

`XXX = YYY`

where `XXX` is a property and `YYY` is the value or values associated
with it (the spaces are optional). For example:

```
[1]
Name = Bulbasaur  
InternalName = BULBASAUR  
Type1 = GRASS  
Type2 = POISON  
BaseStats = 45,49,49,45,65,65  
GenderRate = FemaleOneEighth  
BaseEXP = 64  
Moves = 1,TACKLE,3,GROWL,7,LEECHSEED,9,VINEWHIP,13,POISONPOWDER,13,SLEEPPOWDER,15,TAKEDOWN,19,RAZORLEAF,21,SWEETSCENT,25,GROWTH,27,DOUBLEEDGE,31,WORRYSEED,33,SYNTHESIS,37,SEEDBOMB  
Height = 0.7  
Pokedex = Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.  
Evolutions = IVYSAUR,Level,16
```

The only required lines of information are the `Name` and the
`InternalName`. All other pieces of information are optional, but most
of them will have default values if they are not defined. The order of
the lines does not matter, except for the ID number line in square
brackets which must be first.

<table>
	<thead>
	<tr class="header">
	<th><p>Data</p></th>
	<th><p>Description</p></th>
	<th><p>Default value</p></th>
	</tr>
	</thead>
	<tbody>
	<tr class="odd">
	<td><p>[ID number]</p></td>
	<td><p>This line must come first in a section, because, as mentioned
	above, this line defines when a new section begins. This line contains a
	number inside square brackets, e.g. <code>[42]</code>.</p>
	<p>This number must be different for each species. It must be a whole
	number greater than 0. You cannot skip numbers. The ID number is used as
	the <a href="Pokédex" title="wikilink">National Pokédex</a> number, and
	also affects the order in which species are listed in some <a
	href="Debug_mode" title="wikilink">Debug mode</a> features.</p></td>
	<td><p>n/a</p></td>
	</tr>
	<tr class="even">
	<td><p>Name</p></td>
	<td><p>The name of the species, as seen by the player.</p></td>
	<td><p>This line is required</p></td>
	</tr>
	<tr class="odd">
	<td><p>InternalName</p></td>
	<td><p>This must be different for each species. Also known as the ID,
	this is how the scripts refer to the species. Typically this is the same
	as the species name, but written in all capital letters and with no
	spaces or symbols. In the scripts, the ID is used as a symbol (i.e. with
	a colon in front of it, e.g. :BULBASAUR). The ID is never seen by the
	player.</p></td>
	<td><p>This line is required</p></td>
	</tr>
	<tr class="even">
	<td><p>Type1<br />
	Type2</p></td>
	<td><p>The ID of the primary and secondary <a href="Defining_a_type"
	title="wikilink">elemental types</a> of the species.</p></td>
	<td><p>NORMAL (for Type1)</p></td>
	</tr>
	<tr class="odd">
	<td><p>BaseStats</p></td>
	<td><p>Six comma-separated values, corresponding to the order that main
	stats are defined. By default, the order is:</p>
	<ol>
	<li>HP</li>
	<li>Attack</li>
	<li>Defense</li>
	<li>Speed</li>
	<li>Special Attack</li>
	<li>Special Defense</li>
	</ol>
	<p>Each value can be 1 or higher.</p></td>
	<td><p>1,1,1,1,1,1</p></td>
	</tr>
	<tr class="even">
	<td><p>GenderRate</p></td>
	<td><p>The likelihood of a Pokémon of the species being a certain
	gender. Must be one of the following:</p>
	<ul>
	<li>AlwaysMale</li>
	<li>FemaleOneEighth</li>
	<li>Female25Percent</li>
	<li>Female50Percent</li>
	<li>Female75Percent</li>
	<li>FemaleSevenEighths</li>
	<li>AlwaysFemale</li>
	<li>Genderless</li>
	</ul></td>
	<td><p>Female50Percent</p></td>
	</tr>
	<tr class="odd">
	<td><p>GrowthRate</p></td>
	<td><p>The rate at which a Pokémon of the species gains levels (i.e. how
	much Experience is needed to level up). Must be one of the
	following:</p>
	<ul>
	<li>Fast</li>
	<li>Medium (known elsewhere as Medium Fast)</li>
	<li>Slow</li>
	<li>Parabolic (known elsewhere as Medium Slow)</li>
	<li>Erratic</li>
	<li>Fluctuating</li>
	</ul></td>
	<td><p>Medium</p></td>
	</tr>
	<tr class="even">
	<td><p>BaseEXP</p></td>
	<td><p>The base amount of Experience gained from <a
	href="Ending_a_battle" title="wikilink">defeating a Pokémon</a> of the
	species. It must be a whole number that is 1 or higher.</p>
	<p>This base amount is used in a calculation to determine the actual
	number of Exp. points awarded for defeating a Pokémon of the
	species.</p></td>
	<td><p>100</p></td>
	</tr>
	<tr class="odd">
	<td><p>EffortPoints</p></td>
	<td><p>The number of EVs gained by defeating a Pokémon of the species.
	Is six comma-separated values, corresponding to the order that main
	stats are defined. By default, the order is:</p>
	<ol>
	<li>HP</li>
	<li>Attack</li>
	<li>Defense</li>
	<li>Speed</li>
	<li>Special Attack</li>
	<li>Special Defense</li>
	</ol>
	<p>Each value can be 0 or higher. As a rule, the total of these numbers
	should be between 1 and 3, and higher evolutions tend to give more
	EVs.</p></td>
	<td><p>0,0,0,0,0,0</p></td>
	</tr>
	<tr class="even">
	<td><p>Rareness</p></td>
	<td><p>The catch rate of the species. It can be 0 or higher (typically
	the highest is 255). The higher the number, the more likely a capture (0
	means it cannot be caught by anything except a Master Ball).</p></td>
	<td><p>255</p></td>
	</tr>
	<tr class="odd">
	<td><p>Happiness</p></td>
	<td><p>The amount of happiness a newly caught Pokémon of the species
	will have. It can be 0 or higher, although it is typically 70. The game
	treats 255 as the highest attainable happiness.</p></td>
	<td><p>70</p></td>
	</tr>
	<tr class="even">
	<td><p>Abilities</p></td>
	<td><p>The IDs of one or two <a href="abilities"
	title="wikilink">abilities</a> that the species can have. If there are
	two abilities, separate them with a comma.</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="odd">
	<td><p>HiddenAbility</p></td>
	<td><p>The IDs of any number of additional <a href="abilities"
	title="wikilink">abilities</a> that the species can have. If there are
	multiple abilities here, they are separated by commas.</p>
	<p>Pokémon cannot have any Hidden Ability naturally, and must be <a
	href="Editing_a_Pokémon" title="wikilink">specially given
	one</a>.</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="even">
	<td><p>Moves</p></td>
	<td><p>The <a href="moves" title="wikilink">moves</a> that all Pokémon
	of the species learn as they level up. This line consists of
	comma-separated level/move pairs which are themselves comma-separated,
	i.e. <code>level,move,level,move,level,move...</code>. Each pair
	contains the level at which the Pokémon will learn the move, followed by
	the ID of the move it will learn.</p>
	<p>A level of 0 means the move will be learned when a Pokémon evolves
	into the species, and not at any other point (except via the <a
	href="Special_NPCs" title="wikilink">Move Relearner</a>).</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="odd">
	<td><p>TutorMoves</p></td>
	<td><p>A comma-separated list of the IDs of <a href="moves"
	title="wikilink">moves</a> that a Pokémon of the species can be taught
	by a <a href="Learning_moves" title="wikilink">HM, TM, TR or Move
	Tutor</a>. If a move is not listed here, it cannot be taught by those
	methods, even if the move appears in its Moves or EggMoves
	properties.</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="even">
	<td><p>EggMoves</p></td>
	<td><p>A comma-separated list of the IDs of <a href="moves"
	title="wikilink">moves</a> that a Pokémon of the species can only learn
	as an <a href="Eggs" title="wikilink">egg</a> (obtained through <a
	href="breeding" title="wikilink">breeding</a>). Only species that can be
	in eggs should have this line (typically only unevolved
	species).</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="odd">
	<td><p>Compatibility</p></td>
	<td><p>The <a href="Breeding" title="wikilink">egg group</a>(s) that the
	species belongs to. If there are multiple egg groups here, they are
	separated by commas. The default available egg group are:</p>
	<ul>
	<li>Monster</li>
	<li>Water1</li>
	<li>Bug</li>
	<li>Flying</li>
	<li>Field</li>
	<li>Fairy</li>
	<li>Grass</li>
	<li>Humanlike</li>
	<li>Water3</li>
	<li>Mineral</li>
	<li>Amorphous</li>
	<li>Water2</li>
	<li>Ditto</li>
	<li>Dragon</li>
	<li>Undiscovered</li>
	</ul>
	<p>"Water1" is for sea creatures, "Water2" is for fish, and "Water3" is
	for shellfish. "Ditto" should contain only Ditto, as a species in that
	group can breed with any other breedable Pokémon. If any egg group is
	"Undiscovered", the species cannot breed.</p></td>
	<td><p>Undiscovered</p></td>
	</tr>
	<tr class="even">
	<td><p>StepsToHatch</p></td>
	<td><p>The number of steps it takes to hatch an <a href="Eggs"
	title="wikilink">egg</a> of the species. It can be 1 or higher. Note
	that this is <em>not</em> the number of egg cycles for the species, but
	the actual number of steps. Only species that can be in eggs should have
	this line (typically only unevolved species).</p></td>
	<td><p>1</p></td>
	</tr>
	<tr class="odd">
	<td><p>Height</p></td>
	<td><p>The height of the species in meters, to one decimal place. Use a
	period for the decimal point, and do not use commas for thousands.</p>
	<p>The <a href="Pokédex" title="wikilink">Pokédex</a> will automatically
	show this height in feet/inches if the game recognises that the player
	is in the USA. This is only cosmetic; the rest of the scripts still
	perform calculations using the meters value defined.</p></td>
	<td><p>0.1</p></td>
	</tr>
	<tr class="even">
	<td><p>Weight</p></td>
	<td><p>The weight of the species in kilograms, to one decimal place. Use
	a period for the decimal point, and do not use commas for thousands.</p>
	<p>The <a href="Pokédex" title="wikilink">Pokédex</a> will automatically
	show this weight in pounds if the game recognises that the player is in
	the USA. This is only cosmetic; the rest of the scripts still perform
	calculations using the kilograms value defined.</p></td>
	<td><p>0.1</p></td>
	</tr>
	<tr class="odd">
	<td><p>Color</p></td>
	<td><p>The main body color of the species. The default available body
	colors are:</p>
	<ul>
	<li>Black</li>
	<li>Blue</li>
	<li>Brown</li>
	<li>Gray</li>
	<li>Green</li>
	<li>Pink</li>
	<li>Purple</li>
	<li>Red</li>
	<li>White</li>
	<li>Yellow</li>
	</ul></td>
	<td><p>Red</p></td>
	</tr>
	<tr class="even">
	<td><p>Shape</p></td>
	<td><p>The body shape of the species. The <a href="Pokédex"
	title="wikilink">Pokédex</a> can search for Pokémon of particular
	shapes. The default available body shapes are:</p>
	<ul>
	<li>Head</li>
	<li>Serpentine</li>
	<li>Finned</li>
	<li>HeadArms</li>
	<li>HeadBase</li>
	<li>BipedalTail</li>
	<li>HeadLegs</li>
	<li>Quadruped</li>
	<li>Winged</li>
	<li>Multiped</li>
	<li>MultiBody</li>
	<li>Bipedal</li>
	<li>MultiWinged</li>
	<li>Insectoid</li>
	</ul></td>
	<td><p>Head</p></td>
	</tr>
	<tr class="odd">
	<td><p>Habitat</p></td>
	<td><p>The kind of location that the species can typically be found in.
	The default available habitats are:</p>
	<ul>
	<li>None</li>
	<li>Cave</li>
	<li>Forest</li>
	<li>Grassland</li>
	<li>Mountain</li>
	<li>Rare</li>
	<li>RoughTerrain</li>
	<li>Sea</li>
	<li>Urban</li>
	<li>WatersEdge</li>
	</ul>
	<p>"Rare" can be taken to mean "unknown" here.</p>
	<p>This information is unused in Essentials.</p></td>
	<td><p>None</p></td>
	</tr>
	<tr class="even">
	<td><p>Kind</p></td>
	<td><p>The species' category, which is displayed in the <a
	href="Pokédex" title="wikilink">Pokédex</a>. For example, Bulbasaur is
	the Seed Pokémon. The word "Pokémon" is automatically added to the end,
	so only "Seed" needs to be here.</p></td>
	<td><p>"???"</p></td>
	</tr>
	<tr class="odd">
	<td><p>Pokedex</p></td>
	<td><p>The <a href="Pokédex" title="wikilink">Pokédex</a>
	entry.</p></td>
	<td><p>"???"</p></td>
	</tr>
	<tr class="even">
	<td><p>FormName</p></td>
	<td><p>The name of this <a href="Forms" title="wikilink">form</a> of the
	species (form 0), if it has one.</p>
	<p>If this is blank, then its form name as shown in the <a
	href="Pokédex" title="wikilink">Pokédex</a>'s Forms page will be
	"Male"/"Female" if the species is gendered. If the species is
	genderless, its form name will instead be "Genderless" (if this is the
	only form for the species) or "One Form" (if the species also has other
	forms).</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="odd">
	<td><p>Generation</p></td>
	<td><p>A number representing the generation of Pokémon games in which
	this species first appeared. This information is unused in
	Essentials.</p></td>
	<td><p>0</p></td>
	</tr>
	<tr class="even">
	<td><p>WildItemCommon<br />
	WildItemUncommon<br />
	WildItemRare</p></td>
	<td><p>The IDs of <a href="items" title="wikilink">items</a> that a wild
	Pokémon of the species may be found holding. Each line can only have one
	item.</p>
	<p>The chances of holding the item are 50%, 5% and 1% respectively. If
	all three are the same item, then the chance of holding it is 100%
	instead.</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="odd">
	<td><p>BattlerPlayerX<br />
	BattlerPlayerY</p></td>
	<td><p>Affects the positioning of the back sprite of the species in <a
	href="Battles" title="wikilink">battle</a>. A higher number means the
	back sprite is placed further right/lower down in the screen. Can be
	positive or negative.</p></td>
	<td><p>0</p></td>
	</tr>
	<tr class="even">
	<td><p>BattlerEnemyX<br />
	BattlerEnemyY</p></td>
	<td><p>Affects the positioning of the front sprite of the species in <a
	href="Battles" title="wikilink">battle</a>. A higher number means the
	front sprite is placed further right/lower down in the screen. Can be
	positive or negative.</p></td>
	<td><p>0</p></td>
	</tr>
	<tr class="odd">
	<td><p>BattlerAltitude</p></td>
	<td><p>Affects the positioning of the front sprite of the species in <a
	href="Battles" title="wikilink">battle</a> relative to its base. A
	higher number means the front sprite is placed further up the screen.
	Can only be positive or 0.</p>
	<p>This property is typically unused because <code>BattlerEnemyY</code>
	can do the same thing.</p></td>
	<td><p>0</p></td>
	</tr>
	<tr class="even">
	<td><p>BattlerShadowX</p></td>
	<td><p>Affects the horizontal positioning of the shadow beneath the
	front sprite of the species in <a href="Battles"
	title="wikilink">battle</a>. A higher number means the shadow is placed
	further right on the screen. Can be positive or negative.</p></td>
	<td><p>0</p></td>
	</tr>
	<tr class="odd">
	<td><p>BattlerShadowSize</p></td>
	<td><p>A number that determines which shadow graphic to place underneath
	the front sprite of the species in <a href="Battles"
	title="wikilink">battle</a>. It can be 0 or higher. By default, there
	are three possible shadow graphics (in the folder
	"Graphics/Pokemon/Shadow"), ranging from 1 (smallest) to 3
	(largest).</p></td>
	<td><p>2</p></td>
	</tr>
	<tr class="even">
	<td><p>Evolutions</p></td>
	<td><p>The <a href="evolution" title="wikilink">evolution</a> paths the
	species can take. For each possible evolution of the species, there are
	three parts:</p>
	<ol>
	<li>The ID of the species it evolves into.</li>
	<li>The evolution method. Must be one of the methods registered in
	<code>GameData::Evolution</code>. A full list is on the page <a
	href="Evolution" title="wikilink">Evolution</a>, but examples are:
	<ul>
	<li>Level</li>
	<li>LevelFemale</li>
	<li>Happiness</li>
	<li>Beauty</li>
	<li>HasMove</li>
	<li>Location</li>
	<li>Item</li>
	<li>Trade</li>
	</ul></li>
	<li>A parameter used by the evolution method. Depending on the method,
	this could be blank or a number or the ID of a
	move/item/ability/species/type/etc.</li>
	</ol>
	<p>If there are multiple evolution paths, they are separated by commas.
	The three parts of each evolution path are also separated by commas. Be
	careful to include the correct number of commas when writing an
	evolution path whose method doesn't use a parameter.</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	<tr class="odd">
	<td><p>Incense</p></td>
	<td><p>The ID of an item that needs to be held by a parent when <a
	href="breeding" title="wikilink">breeding</a> in order for the <a
	href="Eggs" title="wikilink">egg</a> to be this species. If neither
	parent is holding the required item, the egg will be the next evolved
	species instead.</p>
	<p>The only species that should have this line are ones which cannot
	breed, but which evolve into a species that can. That is, the species
	should be a "baby" species. Not all baby species need this line. Note
	that Essentials does not have any formal definition of what a "baby"
	species is.</p></td>
	<td><p><em>none</em></p></td>
	</tr>
	</tbody>
</table>

## Graphics and audio

A Pokémon species has one of each of the following:

-   Four battle sprites, used in a variety of places in-game (they can
    be any size):
    1.  Front normal
    2.  Rear normal
    3.  Front shiny
    4.  Rear shiny
-   A two-frame icon (each frame is square, with the second frame placed
    to the right of the first). Used mainly in the
    [party](party "wikilink") screen (animated) and [Pokémon
    storage](Pokémon_storage "wikilink") screen (not animated).
-   A graphic depicting its footprint, for use in the
    [Pokédex](Pokédex "wikilink"),
-   An audio file depicting its cry, played in various places,

The battle sprites, icons and footprints all go into corresponding
folders in the folder "Graphics/Pokemon". The names of each of these
graphics are all the same, and are the ID (internal name) of the
species, e.g. "BULBASAUR.png".

A species may have a unique egg sprite. If so, both the sprite and the
icon depicting the egg go in the same folder, which is
"Graphics/Pokemon/Eggs":

-   The egg's sprite will be named as above, e.g. "BULBASAUR.png".
-   The egg's icon will have the suffix "\_icon", e.g.
    "BULBASAUR_icon.png".
-   If the egg has unique crack graphics (shown when the egg is
    hatching), it goes in the same folder and has the suffix "\_cracks",
    e.g. "BULBASAUR_cracks.png". If the egg does not have unique crack
    graphics, it will use the "000_cracks.png" graphic instead.

It is not possible to have different egg graphics for shiny Pokémon.

The shiny versions of the battle sprites and icon are not necessary. If
they do not exist, the regular versions will be used instead.

The cry file is placed in the folder "Audio/SE/Cries" with the same name
as above (e.g. "BULBASAUR.wav"), and can be of any supported audio type.

### Female differences

Female Pokémon can have different sprites/icons to male Pokémon of the
same species. If so, they are placed in the same folders as the male
versions of those sprites/icons, but they have the filename suffix
"\_female", e.g. "BULBASAUR_female.png".

Female Pokémon of a species cannot have different egg sprites/icons,
footprint graphics or cries to the males.

## Multiple forms

If a Pokémon species has more than one form (including having
mechanically different male/female versions, and Mega Evolutions), then
it will need additional graphics and possibly additional cries to depict
them.

Alternate forms are defined in the [PBS file](PBS_file "wikilink")
"pokemonforms.txt", which is laid out in much the same way as
"pokemon.txt".