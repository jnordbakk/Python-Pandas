
Heroes Of Pymoli Data Analysis:

-Of the 780 active players, the vast majority are male (81%). There also exists, a smaller, but notable proportion of female players (17%).

-Our peak age demographic falls between 20-24 (33.21%) with spending a total of $$978.77. 

-The secondary group falls between 15-19 (12.82%) and 25-29 (11.15%).

-The most profitable games are on the higher end of the price range ($3.00-$4.50)


```
# Import Dependencies
import pandas as pd
import os
```


```
# Create dataframe with player data
player_dicts= [{"SN":"Aelalis34","Age":38,"Gender":"Male","Item ID":165,"Item Name":"Bone Crushing Silver Skewer","Price":3.37},{"SN":"Eolo46","Age":21,"Gender":"Male","Item ID":119,"Item Name":"Stormbringer, Dark Blade of Ending Misery","Price":2.32},{"SN":"Assastnya25","Age":34,"Gender":"Male","Item ID":174,"Item Name":"Primitive Blade","Price":2.46},{"SN":"Pheusrical25","Age":21,"Gender":"Male","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Aela59","Age":23,"Gender":"Male","Item ID":63,"Item Name":"Stormfury Mace","Price":1.27},{"SN":"Tanimnya91","Age":20,"Gender":"Male","Item ID":10,"Item Name":"Sleepwalker","Price":1.73},{"SN":"Undjaskla97","Age":20,"Gender":"Male","Item ID":153,"Item Name":"Mercenary Sabre","Price":4.57},{"SN":"Iathenudil29","Age":29,"Gender":"Female","Item ID":169,"Item Name":"Interrogator, Blood Blade of the Queen","Price":3.32},{"SN":"Sondenasta63","Age":25,"Gender":"Male","Item ID":118,"Item Name":"Ghost Reaver, Longsword of Magic","Price":2.77},{"SN":"Hilaerin92","Age":31,"Gender":"Male","Item ID":99,"Item Name":"Expiration, Warscythe Of Lost Worlds","Price":4.53},{"SN":"Chamosia29","Age":24,"Gender":"Male","Item ID":57,"Item Name":"Despair, Favor of Due Diligence","Price":3.81},{"SN":"Sally64","Age":20,"Gender":"Male","Item ID":47,"Item Name":"Alpha, Reach of Ending Hope","Price":1.55},{"SN":"Iskossa88","Age":30,"Gender":"Male","Item ID":81,"Item Name":"Dreamkiss","Price":4.06},{"SN":"Seorithstilis90","Age":23,"Gender":"Male","Item ID":77,"Item Name":"Piety, Guardian of Riddles","Price":3.68},{"SN":"Sundast29","Age":40,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Haellysu29","Age":21,"Gender":"Male","Item ID":96,"Item Name":"Blood-Forged Skeletal Spine","Price":4.77},{"SN":"Sundista85","Age":22,"Gender":"Female","Item ID":123,"Item Name":"Twilight's Carver","Price":1.14},{"SN":"Aenarap34","Age":22,"Gender":"Female","Item ID":59,"Item Name":"Lightning, Etcher of the King","Price":1.65},{"SN":"Iskista88","Age":28,"Gender":"Male","Item ID":91,"Item Name":"Celeste","Price":3.71},{"SN":"Assossa43","Age":31,"Gender":"Male","Item ID":177,"Item Name":"Winterthorn, Defender of Shifting Worlds","Price":4.89},{"SN":"Irith83","Age":24,"Gender":"Male","Item ID":78,"Item Name":"Glimmer, Ender of the Moon","Price":2.33},{"SN":"Iaralrgue74","Age":15,"Gender":"Male","Item ID":3,"Item Name":"Phantomlight","Price":1.79},{"SN":"Deural48","Age":11,"Gender":"Female","Item ID":11,"Item Name":"Brimstone","Price":2.52},{"SN":"Chanosia65","Age":19,"Gender":"Male","Item ID":183,"Item Name":"Dragon's Greatsword","Price":2.36},{"SN":"Qarwen67","Age":11,"Gender":"Male","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Idai61","Age":21,"Gender":"Male","Item ID":63,"Item Name":"Stormfury Mace","Price":1.27},{"SN":"Aerithllora36","Age":29,"Gender":"Male","Item ID":132,"Item Name":"Persuasion","Price":3.9},{"SN":"Assastnya25","Age":34,"Gender":"Male","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Ilariarin45","Age":15,"Gender":"Male","Item ID":49,"Item Name":"The Oculus, Token of Lost Worlds","Price":4.23},{"SN":"Phaedai25","Age":16,"Gender":"Female","Item ID":45,"Item Name":"Glinting Glass Edge","Price":2.46},{"SN":"Eulaeria40","Age":21,"Gender":"Female","Item ID":155,"Item Name":"War-Forged Gold Deflector","Price":3.73},{"SN":"Iarilis73","Age":18,"Gender":"Male","Item ID":37,"Item Name":"Shadow Strike, Glory of Ending Hope","Price":1.93},{"SN":"Malunil62","Age":19,"Gender":"Male","Item ID":48,"Item Name":"Rage, Legacy of the Lone Victor","Price":4.32},{"SN":"Iskimnya76","Age":24,"Gender":"Male","Item ID":90,"Item Name":"Betrayer","Price":1.67},{"SN":"Yararmol43","Age":22,"Gender":"Male","Item ID":47,"Item Name":"Alpha, Reach of Ending Hope","Price":1.55},{"SN":"Aisur51","Age":21,"Gender":"Female","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Undare39","Age":20,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Sondossa91","Age":31,"Gender":"Male","Item ID":171,"Item Name":"Scalpel","Price":3.62},{"SN":"Chamjasknya65","Age":20,"Gender":"Male","Item ID":25,"Item Name":"Hero Cane","Price":1.03},{"SN":"Lassilsa63","Age":23,"Gender":"Male","Item ID":63,"Item Name":"Stormfury Mace","Price":1.27},{"SN":"Tyisur83","Age":32,"Gender":"Male","Item ID":7,"Item Name":"Thorn, Satchel of Dark Souls","Price":4.51},{"SN":"Aeral43","Age":19,"Gender":"Female","Item ID":124,"Item Name":"Venom Claymore","Price":2.72},{"SN":"Lassadarsda57","Age":24,"Gender":"Male","Item ID":25,"Item Name":"Hero Cane","Price":1.03},{"SN":"Alaephos75","Age":22,"Gender":"Male","Item ID":68,"Item Name":"Storm-Weaver, Slayer of Inception","Price":2.49},{"SN":"Frichjask31","Age":22,"Gender":"Male","Item ID":85,"Item Name":"Malificent Bag","Price":2.17},{"SN":"Eusur90","Age":20,"Gender":"Male","Item ID":120,"Item Name":"Agatha","Price":1.91},{"SN":"Palatyon26","Age":11,"Gender":"Male","Item ID":17,"Item Name":"Lazarus, Terror of the Earth","Price":3.47},{"SN":"Saellyra72","Age":24,"Gender":"Male","Item ID":141,"Item Name":"Persuasion","Price":3.27},{"SN":"Ililsa62","Age":20,"Gender":"Male","Item ID":73,"Item Name":"Ritual Mace","Price":3.74},{"SN":"Eosur70","Age":22,"Gender":"Male","Item ID":151,"Item Name":"Severance","Price":1.85},{"SN":"Saistyphos30","Age":32,"Gender":"Female","Item ID":32,"Item Name":"Orenmir","Price":4.95},{"SN":"Reula64","Age":16,"Gender":"Male","Item ID":169,"Item Name":"Interrogator, Blood Blade of the Queen","Price":3.32},{"SN":"Chanirrala39","Age":24,"Gender":"Male","Item ID":165,"Item Name":"Bone Crushing Silver Skewer","Price":3.37},{"SN":"Chadanto83","Age":22,"Gender":"Male","Item ID":51,"Item Name":"Endbringer","Price":2.67},{"SN":"Minduli80","Age":25,"Gender":"Female","Item ID":101,"Item Name":"Final Critic","Price":4.62},{"SN":"Heunadil74","Age":24,"Gender":"Male","Item ID":140,"Item Name":"Striker","Price":3.82},{"SN":"Marilsasya33","Age":23,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Alallo58","Age":24,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Tyaeristi78","Age":24,"Gender":"Female","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Ila44","Age":15,"Gender":"Male","Item ID":2,"Item Name":"Verdict","Price":3.4},{"SN":"Iskossaya95","Age":31,"Gender":"Male","Item ID":86,"Item Name":"Stormfury Lantern","Price":1.28},{"SN":"Rinallorap73","Age":24,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Aeri84","Age":19,"Gender":"Female","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Ryanara76","Age":23,"Gender":"Male","Item ID":28,"Item Name":"Flux, Destroyer of Due Diligence","Price":3.04},{"SN":"Syally44","Age":15,"Gender":"Male","Item ID":160,"Item Name":"Azurewrath","Price":2.22},{"SN":"Shaidanu32","Age":15,"Gender":"Male","Item ID":134,"Item Name":"Undead Crusader","Price":4.67},{"SN":"Syasriria69","Age":18,"Gender":"Male","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Lisiriya82","Age":25,"Gender":"Male","Item ID":83,"Item Name":"Lifebender","Price":3.51},{"SN":"Qarwen67","Age":11,"Gender":"Male","Item ID":38,"Item Name":"The Void, Vengeance of Dark Magic","Price":2.82},{"SN":"Iskosia51","Age":15,"Gender":"Male","Item ID":7,"Item Name":"Thorn, Satchel of Dark Souls","Price":4.51},{"SN":"Eosurdru76","Age":7,"Gender":"Female","Item ID":158,"Item Name":"Darkheart, Butcher of the Champion","Price":3.56},{"SN":"Lassimla92","Age":21,"Gender":"Male","Item ID":85,"Item Name":"Malificent Bag","Price":2.17},{"SN":"Tauldilsa43","Age":34,"Gender":"Male","Item ID":110,"Item Name":"Suspension","Price":2.11},{"SN":"Erudrion71","Age":16,"Gender":"Male","Item ID":122,"Item Name":"Unending Tyranny","Price":1.21},{"SN":"Chanjaskan37","Age":20,"Gender":"Male","Item ID":54,"Item Name":"Eternal Cleaver","Price":3.14},{"SN":"Sondastan54","Age":31,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Strithenu87","Age":20,"Gender":"Male","Item ID":105,"Item Name":"Hailstorm Shadowsteel Scythe","Price":3.73},{"SN":"Chanastsda67","Age":15,"Gender":"Male","Item ID":87,"Item Name":"Deluge, Edge of the West","Price":2.2},{"SN":"Baelollodeu94","Age":23,"Gender":"Male","Item ID":23,"Item Name":"Crucifer","Price":2.77},{"SN":"Undirrala66","Age":29,"Gender":"Male","Item ID":144,"Item Name":"Blood Infused Guardian","Price":2.86},{"SN":"Chanosseya79","Age":16,"Gender":"Female","Item ID":128,"Item Name":"Blazeguard, Reach of Eternity","Price":4.0},{"SN":"Yaristi64","Age":38,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Airi27","Age":23,"Gender":"Male","Item ID":46,"Item Name":"Hopeless Ebon Dualblade","Price":4.75},{"SN":"Frichaststa61","Age":25,"Gender":"Female","Item ID":32,"Item Name":"Orenmir","Price":4.95},{"SN":"Raysistast71","Age":25,"Gender":"Male","Item ID":7,"Item Name":"Thorn, Satchel of Dark Souls","Price":4.51},{"SN":"Ithergue48","Age":20,"Gender":"Female","Item ID":150,"Item Name":"Deathraze","Price":4.54},{"SN":"Chanastst38","Age":27,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Sundosiasta28","Age":22,"Gender":"Male","Item ID":108,"Item Name":"Extraction, Quickblade Of Trembling Hands","Price":3.39},{"SN":"Undotesta33","Age":23,"Gender":"Male","Item ID":132,"Item Name":"Persuasion","Price":3.9},{"SN":"Tyiaduenuru55","Age":22,"Gender":"Male","Item ID":172,"Item Name":"Blade of the Grave","Price":1.69},{"SN":"Iskjaskst81","Age":33,"Gender":"Male","Item ID":91,"Item Name":"Celeste","Price":3.71},{"SN":"Iskjaskan81","Age":24,"Gender":"Male","Item ID":167,"Item Name":"Malice, Legacy of the Queen","Price":2.38},{"SN":"Frichim27","Age":24,"Gender":"Male","Item ID":181,"Item Name":"Reaper's Toll","Price":4.56},{"SN":"Hailaphos89","Age":20,"Gender":"Male","Item ID":20,"Item Name":"Netherbane","Price":1.48},{"SN":"Seorithstilis90","Age":23,"Gender":"Male","Item ID":130,"Item Name":"Alpha","Price":1.56},{"SN":"Jiskjask80","Age":24,"Gender":"Male","Item ID":111,"Item Name":"Misery's End","Price":2.91},{"SN":"Yasurra52","Age":22,"Gender":"Female","Item ID":54,"Item Name":"Eternal Cleaver","Price":3.14},{"SN":"Assassasta79","Age":17,"Gender":"Female","Item ID":49,"Item Name":"The Oculus, Token of Lost Worlds","Price":4.23},{"SN":"Lamyon68","Age":25,"Gender":"Male","Item ID":47,"Item Name":"Alpha, Reach of Ending Hope","Price":1.55},{"SN":"Alo67","Age":20,"Gender":"Male","Item ID":110,"Item Name":"Suspension","Price":2.11},{"SN":"Farenon57","Age":20,"Gender":"Male","Item ID":103,"Item Name":"Singed Scalpel","Price":4.87},{"SN":"Assistasda90","Age":25,"Gender":"Male","Item ID":30,"Item Name":"Stormcaller","Price":4.15},{"SN":"Frichaya88","Age":30,"Gender":"Male","Item ID":51,"Item Name":"Endbringer","Price":2.67},{"SN":"Marassanya92","Age":27,"Gender":"Male","Item ID":139,"Item Name":"Mercy, Katana of Dismay","Price":4.37},{"SN":"Iskista96","Age":34,"Gender":"Male","Item ID":173,"Item Name":"Stormfury Longsword","Price":4.83},{"SN":"Mindirra92","Age":20,"Gender":"Male","Item ID":55,"Item Name":"Vindictive Glass Edge","Price":4.26},{"SN":"Chadossa56","Age":37,"Gender":"Female","Item ID":174,"Item Name":"Primitive Blade","Price":2.46},{"SN":"Undirrala66","Age":29,"Gender":"Male","Item ID":115,"Item Name":"Spectral Diamond Doomblade","Price":4.25},{"SN":"Eoda93","Age":22,"Gender":"Male","Item ID":35,"Item Name":"Heartless Bone Dualblade","Price":2.63},{"SN":"Lassast89","Age":20,"Gender":"Female","Item ID":42,"Item Name":"The Decapitator","Price":4.82},{"SN":"Philodil43","Age":20,"Gender":"Female","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Tyirithnu40","Age":19,"Gender":"Male","Item ID":160,"Item Name":"Azurewrath","Price":2.22},{"SN":"Haerith37","Age":25,"Gender":"Male","Item ID":57,"Item Name":"Despair, Favor of Due Diligence","Price":3.81},{"SN":"Jeyciman68","Age":20,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Chamirraya83","Age":20,"Gender":"Male","Item ID":130,"Item Name":"Alpha","Price":1.56},{"SN":"Yasur85","Age":23,"Gender":"Male","Item ID":9,"Item Name":"Thorn, Conqueror of the Corrupted","Price":2.04},{"SN":"Koikirra25","Age":25,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Qarwen67","Age":11,"Gender":"Male","Item ID":160,"Item Name":"Azurewrath","Price":2.22},{"SN":"Quarunarn52","Age":23,"Gender":"Male","Item ID":46,"Item Name":"Hopeless Ebon Dualblade","Price":4.75},{"SN":"Yasur35","Age":19,"Gender":"Male","Item ID":180,"Item Name":"Stormcaller","Price":2.78},{"SN":"Isurriarap71","Age":31,"Gender":"Male","Item ID":102,"Item Name":"Avenger","Price":4.16},{"SN":"Lassjask63","Age":7,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Iliel92","Age":18,"Gender":"Female","Item ID":53,"Item Name":"Vengeance Cleaver","Price":3.7},{"SN":"Arithllorin55","Age":19,"Gender":"Male","Item ID":73,"Item Name":"Ritual Mace","Price":3.74},{"SN":"Silideu44","Age":22,"Gender":"Male","Item ID":18,"Item Name":"Torchlight, Bond of Storms","Price":1.77},{"SN":"Heosurnuru52","Age":7,"Gender":"Female","Item ID":10,"Item Name":"Sleepwalker","Price":1.73},{"SN":"Raesty92","Age":25,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Eyircil84","Age":23,"Gender":"Female","Item ID":74,"Item Name":"Yearning Crusher","Price":1.06},{"SN":"Isursti83","Age":24,"Gender":"Male","Item ID":140,"Item Name":"Striker","Price":3.82},{"SN":"Eurinu48","Age":23,"Gender":"Female","Item ID":126,"Item Name":"Exiled Mithril Longsword","Price":3.25},{"SN":"Saedaiphos46","Age":24,"Gender":"Male","Item ID":50,"Item Name":"Dawn","Price":2.55},{"SN":"Undirrala66","Age":29,"Gender":"Male","Item ID":62,"Item Name":"Piece Maker","Price":4.36},{"SN":"Jiskossa51","Age":23,"Gender":"Male","Item ID":125,"Item Name":"Whistling Mithril Warblade","Price":4.32},{"SN":"Sundossast30","Age":17,"Gender":"Female","Item ID":108,"Item Name":"Extraction, Quickblade Of Trembling Hands","Price":3.39},{"SN":"Ialallo29","Age":23,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Syasriria69","Age":18,"Gender":"Male","Item ID":68,"Item Name":"Storm-Weaver, Slayer of Inception","Price":2.49},{"SN":"Chanosia60","Age":16,"Gender":"Male","Item ID":121,"Item Name":"Massacre","Price":3.42},{"SN":"Ilosia37","Age":13,"Gender":"Female","Item ID":20,"Item Name":"Netherbane","Price":1.48},{"SN":"Tyeulisu40","Age":28,"Gender":"Male","Item ID":129,"Item Name":"Fate, Vengeance of Eternal Justice","Price":1.55},{"SN":"Yaliru88","Age":22,"Gender":"Male","Item ID":91,"Item Name":"Celeste","Price":3.71},{"SN":"Jiskassa76","Age":25,"Gender":"Male","Item ID":149,"Item Name":"Tranquility, Razor of Black Magic","Price":2.47},{"SN":"Idairin80","Age":24,"Gender":"Male","Item ID":12,"Item Name":"Dawne","Price":4.3},{"SN":"Dyally87","Age":17,"Gender":"Male","Item ID":7,"Item Name":"Thorn, Satchel of Dark Souls","Price":4.51},{"SN":"Quarusrion32","Age":15,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Adairialis76","Age":20,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Lirtilsan89","Age":11,"Gender":"Male","Item ID":71,"Item Name":"Demise","Price":4.07},{"SN":"Reolacal36","Age":23,"Gender":"Male","Item ID":71,"Item Name":"Demise","Price":4.07},{"SN":"Chadanto83","Age":22,"Gender":"Male","Item ID":158,"Item Name":"Darkheart, Butcher of the Champion","Price":3.56},{"SN":"Lisirrast82","Age":18,"Gender":"Male","Item ID":14,"Item Name":"Possessed Core","Price":1.59},{"SN":"Ilrian97","Age":13,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Tyadaru49","Age":25,"Gender":"Male","Item ID":58,"Item Name":"Freak's Bite, Favor of Holy Might","Price":3.03},{"SN":"Sweecossa42","Age":20,"Gender":"Male","Item ID":37,"Item Name":"Shadow Strike, Glory of Ending Hope","Price":1.93},{"SN":"Streural92","Age":13,"Gender":"Male","Item ID":17,"Item Name":"Lazarus, Terror of the Earth","Price":3.47},{"SN":"Queusurra38","Age":23,"Gender":"Male","Item ID":155,"Item Name":"War-Forged Gold Deflector","Price":3.73},{"SN":"Lassilsa41","Age":27,"Gender":"Female","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Aisurphos78","Age":22,"Gender":"Male","Item ID":105,"Item Name":"Hailstorm Shadowsteel Scythe","Price":3.73},{"SN":"Marim28","Age":17,"Gender":"Female","Item ID":27,"Item Name":"Riddle, Tribute of Ended Dreams","Price":3.96},{"SN":"Taeduenu92","Age":20,"Gender":"Male","Item ID":52,"Item Name":"Hatred","Price":4.39},{"SN":"Eodailis27","Age":25,"Gender":"Female","Item ID":66,"Item Name":"Victor Iron Spikes","Price":3.55},{"SN":"Lassjaskan73","Age":20,"Gender":"Male","Item ID":100,"Item Name":"Blindscythe","Price":3.66},{"SN":"Yadanun74","Age":25,"Gender":"Male","Item ID":112,"Item Name":"Worldbreaker","Price":3.29},{"SN":"Iskossasda43","Age":21,"Gender":"Male","Item ID":24,"Item Name":"Warped Fetish","Price":2.41},{"SN":"Aesty51","Age":15,"Gender":"Male","Item ID":94,"Item Name":"Mourning Blade","Price":1.82},{"SN":"Tyida79","Age":23,"Gender":"Male","Item ID":158,"Item Name":"Darkheart, Butcher of the Champion","Price":3.56},{"SN":"Frichossast75","Age":27,"Gender":"Male","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61},{"SN":"Eratiel90","Age":20,"Gender":"Male","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Eoda93","Age":22,"Gender":"Male","Item ID":173,"Item Name":"Stormfury Longsword","Price":4.83},{"SN":"Chamirra53","Age":15,"Gender":"Male","Item ID":86,"Item Name":"Stormfury Lantern","Price":1.28},{"SN":"Alarap40","Age":17,"Gender":"Male","Item ID":124,"Item Name":"Venom Claymore","Price":2.72},{"SN":"Ralaeriadeu65","Age":15,"Gender":"Male","Item ID":102,"Item Name":"Avenger","Price":4.16},{"SN":"Reulae52","Age":9,"Gender":"Male","Item ID":71,"Item Name":"Demise","Price":4.07},{"SN":"Stryanastip77","Age":21,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Iskirra45","Age":21,"Gender":"Male","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Chadadarya31","Age":30,"Gender":"Male","Item ID":0,"Item Name":"Splinter","Price":1.82},{"SN":"Heuli25","Age":24,"Gender":"Male","Item ID":182,"Item Name":"Toothpick","Price":3.48},{"SN":"Raillydeu47","Age":35,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Chamadar61","Age":21,"Gender":"Male","Item ID":182,"Item Name":"Toothpick","Price":3.48},{"SN":"Assassa38","Age":34,"Gender":"Other \/ Non-Disclosed","Item ID":155,"Item Name":"War-Forged Gold Deflector","Price":3.73},{"SN":"Shaidanu32","Age":15,"Gender":"Male","Item ID":97,"Item Name":"Swan Song, Gouger Of Terror","Price":3.58},{"SN":"Chanosiaya39","Age":40,"Gender":"Male","Item ID":70,"Item Name":"Hope's End","Price":3.89},{"SN":"Raeri71","Age":18,"Gender":"Female","Item ID":89,"Item Name":"Blazefury, Protector of Delusions","Price":1.5},{"SN":"Hiasri33","Age":24,"Gender":"Male","Item ID":1,"Item Name":"Crucifer","Price":2.28},{"SN":"Lisossa25","Age":24,"Gender":"Male","Item ID":130,"Item Name":"Alpha","Price":1.56},{"SN":"Sundassa93","Age":23,"Gender":"Female","Item ID":87,"Item Name":"Deluge, Edge of the West","Price":2.2},{"SN":"Rina82","Age":11,"Gender":"Male","Item ID":170,"Item Name":"Shadowsteel","Price":1.98},{"SN":"Siarinum43","Age":22,"Gender":"Male","Item ID":167,"Item Name":"Malice, Legacy of the Queen","Price":2.38},{"SN":"Chanosiaya39","Age":40,"Gender":"Male","Item ID":144,"Item Name":"Blood Infused Guardian","Price":2.86},{"SN":"Eurallo89","Age":20,"Gender":"Female","Item ID":93,"Item Name":"Apocalyptic Battlescythe","Price":3.91},{"SN":"Hirirap39","Age":20,"Gender":"Male","Item ID":78,"Item Name":"Glimmer, Ender of the Moon","Price":2.33},{"SN":"Raillydeu47","Age":35,"Gender":"Male","Item ID":179,"Item Name":"Wolf, Promise of the Moonwalker","Price":1.88},{"SN":"Frichaya88","Age":30,"Gender":"Male","Item ID":36,"Item Name":"Spectral Bone Axe","Price":2.98},{"SN":"Aidaira26","Age":20,"Gender":"Male","Item ID":75,"Item Name":"Brutality Ivory Warmace","Price":1.72},{"SN":"Zontibe81","Age":20,"Gender":"Male","Item ID":91,"Item Name":"Celeste","Price":3.71},{"SN":"Farusrian86","Age":19,"Gender":"Male","Item ID":101,"Item Name":"Final Critic","Price":4.62},{"SN":"Undadarla37","Age":24,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Lirtossa78","Age":14,"Gender":"Male","Item ID":160,"Item Name":"Azurewrath","Price":2.22},{"SN":"Chanirra56","Age":20,"Gender":"Male","Item ID":89,"Item Name":"Blazefury, Protector of Delusions","Price":1.5},{"SN":"Lassast89","Age":20,"Gender":"Female","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Lisasi93","Age":18,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Phadai31","Age":30,"Gender":"Female","Item ID":180,"Item Name":"Stormcaller","Price":2.78},{"SN":"Tyithesura58","Age":22,"Gender":"Male","Item ID":143,"Item Name":"Frenzied Scimitar","Price":2.6},{"SN":"Marilsa48","Age":12,"Gender":"Male","Item ID":137,"Item Name":"Aetherius, Boon of the Blessed","Price":4.75},{"SN":"Siarithria38","Age":24,"Gender":"Male","Item ID":176,"Item Name":"Relentless Iron Skewer","Price":2.97},{"SN":"Lisasi93","Age":18,"Gender":"Male","Item ID":148,"Item Name":"Warmonger, Gift of Suffering's End","Price":3.96},{"SN":"Marirrasta50","Age":19,"Gender":"Male","Item ID":127,"Item Name":"Heartseeker, Reaver of Souls","Price":3.21},{"SN":"Airidil41","Age":17,"Gender":"Male","Item ID":147,"Item Name":"Hellreaver, Heirloom of Inception","Price":3.59},{"SN":"Sausosia74","Age":25,"Gender":"Male","Item ID":161,"Item Name":"Devine","Price":1.45},{"SN":"Yadanun74","Age":25,"Gender":"Male","Item ID":154,"Item Name":"Feral Katana","Price":2.19},{"SN":"Sialaera37","Age":22,"Gender":"Female","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Frichistasta59","Age":33,"Gender":"Other \/ Non-Disclosed","Item ID":157,"Item Name":"Spada, Etcher of Hatred","Price":2.21},{"SN":"Phadue96","Age":22,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Chanirra79","Age":24,"Gender":"Male","Item ID":176,"Item Name":"Relentless Iron Skewer","Price":2.97},{"SN":"Yarmol79","Age":40,"Gender":"Male","Item ID":111,"Item Name":"Misery's End","Price":2.91},{"SN":"Astydil38","Age":24,"Gender":"Male","Item ID":127,"Item Name":"Heartseeker, Reaver of Souls","Price":3.21},{"SN":"Jiskirran77","Age":27,"Gender":"Female","Item ID":148,"Item Name":"Warmonger, Gift of Suffering's End","Price":3.96},{"SN":"Marjasksda39","Age":20,"Gender":"Female","Item ID":154,"Item Name":"Feral Katana","Price":2.19},{"SN":"Eoralphos86","Age":13,"Gender":"Female","Item ID":116,"Item Name":"Renewed Skeletal Katana","Price":2.37},{"SN":"Lisovynya38","Age":18,"Gender":"Male","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Hailaphos89","Age":20,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Frichim77","Age":27,"Gender":"Male","Item ID":148,"Item Name":"Warmonger, Gift of Suffering's End","Price":3.96},{"SN":"Aellyrialis39","Age":33,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Chamilsan75","Age":24,"Gender":"Female","Item ID":61,"Item Name":"Ragnarok","Price":3.97},{"SN":"Saida58","Age":24,"Gender":"Male","Item ID":131,"Item Name":"Fury","Price":4.82},{"SN":"Eusri70","Age":30,"Gender":"Male","Item ID":41,"Item Name":"Orbit","Price":1.16},{"SN":"Aeduera68","Age":26,"Gender":"Male","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Qilatie51","Age":20,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Chamistast30","Age":25,"Gender":"Female","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Qiluard68","Age":20,"Gender":"Male","Item ID":32,"Item Name":"Orenmir","Price":4.95},{"SN":"Tyaelo67","Age":24,"Gender":"Male","Item ID":145,"Item Name":"Fiery Glass Crusader","Price":4.45},{"SN":"Rithe77","Age":26,"Gender":"Female","Item ID":129,"Item Name":"Fate, Vengeance of Eternal Justice","Price":1.55},{"SN":"Tyeosristi57","Age":15,"Gender":"Male","Item ID":140,"Item Name":"Striker","Price":3.82},{"SN":"Lassjaskan73","Age":20,"Gender":"Male","Item ID":125,"Item Name":"Whistling Mithril Warblade","Price":4.32},{"SN":"Eoral49","Age":16,"Gender":"Female","Item ID":60,"Item Name":"Wolf","Price":1.84},{"SN":"Aelollo59","Age":25,"Gender":"Male","Item ID":129,"Item Name":"Fate, Vengeance of Eternal Justice","Price":1.55},{"SN":"Lisossa63","Age":24,"Gender":"Male","Item ID":123,"Item Name":"Twilight's Carver","Price":1.14},{"SN":"Wailin72","Age":35,"Gender":"Male","Item ID":162,"Item Name":"Abyssal Shard","Price":2.04},{"SN":"Yarithllodeu72","Age":22,"Gender":"Male","Item ID":154,"Item Name":"Feral Katana","Price":2.19},{"SN":"Lisistaya47","Age":7,"Gender":"Male","Item ID":121,"Item Name":"Massacre","Price":3.42},{"SN":"Chamadar27","Age":40,"Gender":"Female","Item ID":49,"Item Name":"The Oculus, Token of Lost Worlds","Price":4.23},{"SN":"Ethruard50","Age":24,"Gender":"Female","Item ID":58,"Item Name":"Freak's Bite, Favor of Holy Might","Price":3.03},{"SN":"Lisossa63","Age":24,"Gender":"Male","Item ID":121,"Item Name":"Massacre","Price":3.42},{"SN":"Yathecal72","Age":32,"Gender":"Male","Item ID":135,"Item Name":"Warped Diamond Crusader","Price":4.66},{"SN":"Ilimya66","Age":27,"Gender":"Female","Item ID":182,"Item Name":"Toothpick","Price":3.48},{"SN":"Ialistidru50","Age":21,"Gender":"Male","Item ID":157,"Item Name":"Spada, Etcher of Hatred","Price":2.21},{"SN":"Tyaerith73","Age":21,"Gender":"Other \/ Non-Disclosed","Item ID":183,"Item Name":"Dragon's Greatsword","Price":2.36},{"SN":"Lisistasya93","Age":30,"Gender":"Male","Item ID":8,"Item Name":"Purgatory, Gem of Regret","Price":3.91},{"SN":"Chamadar79","Age":20,"Gender":"Male","Item ID":12,"Item Name":"Dawne","Price":4.3},{"SN":"Haerith37","Age":25,"Gender":"Male","Item ID":23,"Item Name":"Crucifer","Price":2.77},{"SN":"Iallyphos37","Age":20,"Gender":"Male","Item ID":40,"Item Name":"Second Chance","Price":2.34},{"SN":"Tyaelo67","Age":24,"Gender":"Male","Item ID":15,"Item Name":"Soul Infused Crystal","Price":1.03},{"SN":"Ilogha82","Age":25,"Gender":"Male","Item ID":115,"Item Name":"Spectral Diamond Doomblade","Price":4.25},{"SN":"Aeri84","Age":19,"Gender":"Female","Item ID":115,"Item Name":"Spectral Diamond Doomblade","Price":4.25},{"SN":"Ilaesudil92","Age":22,"Gender":"Male","Item ID":1,"Item Name":"Crucifer","Price":2.28},{"SN":"Meosridil82","Age":15,"Gender":"Male","Item ID":149,"Item Name":"Tranquility, Razor of Black Magic","Price":2.47},{"SN":"Undirrasta89","Age":21,"Gender":"Male","Item ID":1,"Item Name":"Crucifer","Price":2.28},{"SN":"Lirtistanya48","Age":27,"Gender":"Male","Item ID":121,"Item Name":"Massacre","Price":3.42},{"SN":"Iadueria43","Age":22,"Gender":"Male","Item ID":17,"Item Name":"Lazarus, Terror of the Earth","Price":3.47},{"SN":"Chanirrala39","Age":24,"Gender":"Male","Item ID":154,"Item Name":"Feral Katana","Price":2.19},{"SN":"Lisjaskan36","Age":25,"Gender":"Female","Item ID":97,"Item Name":"Swan Song, Gouger Of Terror","Price":3.58},{"SN":"Saedue76","Age":25,"Gender":"Male","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Undjasksya56","Age":9,"Gender":"Male","Item ID":99,"Item Name":"Expiration, Warscythe Of Lost Worlds","Price":4.53},{"SN":"Irithrap69","Age":24,"Gender":"Male","Item ID":46,"Item Name":"Hopeless Ebon Dualblade","Price":4.75},{"SN":"Quanenrian83","Age":21,"Gender":"Male","Item ID":29,"Item Name":"Chaos, Ender of the End","Price":3.79},{"SN":"Phenastya51","Age":18,"Gender":"Male","Item ID":137,"Item Name":"Aetherius, Boon of the Blessed","Price":4.75},{"SN":"Marassaya49","Age":45,"Gender":"Male","Item ID":124,"Item Name":"Venom Claymore","Price":2.72},{"SN":"Saellyra72","Age":24,"Gender":"Male","Item ID":8,"Item Name":"Purgatory, Gem of Regret","Price":3.91},{"SN":"Yasrisu92","Age":39,"Gender":"Female","Item ID":143,"Item Name":"Frenzied Scimitar","Price":2.6},{"SN":"Frichistasta59","Age":33,"Gender":"Other \/ Non-Disclosed","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Qilanrion65","Age":15,"Gender":"Male","Item ID":36,"Item Name":"Spectral Bone Axe","Price":2.98},{"SN":"Chanassa48","Age":37,"Gender":"Male","Item ID":72,"Item Name":"Winter's Bite","Price":1.39},{"SN":"Iskassa50","Age":29,"Gender":"Male","Item ID":114,"Item Name":"Yearning Mageblade","Price":1.79},{"SN":"Frichjaskan98","Age":7,"Gender":"Male","Item ID":77,"Item Name":"Piety, Guardian of Riddles","Price":3.68},{"SN":"Sirira97","Age":25,"Gender":"Male","Item ID":117,"Item Name":"Heartstriker, Legacy of the Light","Price":4.15},{"SN":"Eoduenurin62","Age":25,"Gender":"Male","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Yarirarn35","Age":20,"Gender":"Male","Item ID":79,"Item Name":"Alpha, Oath of Zeal","Price":2.88},{"SN":"Yadanun74","Age":25,"Gender":"Male","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61},{"SN":"Aillycal84","Age":12,"Gender":"Other \/ Non-Disclosed","Item ID":128,"Item Name":"Blazeguard, Reach of Eternity","Price":4.0},{"SN":"Eosur70","Age":22,"Gender":"Male","Item ID":128,"Item Name":"Blazeguard, Reach of Eternity","Price":4.0},{"SN":"Chanadar44","Age":29,"Gender":"Male","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61},{"SN":"Lisimsda29","Age":20,"Gender":"Male","Item ID":171,"Item Name":"Scalpel","Price":3.62},{"SN":"Tyidue95","Age":23,"Gender":"Male","Item ID":85,"Item Name":"Malificent Bag","Price":2.17},{"SN":"Yaralnura48","Age":40,"Gender":"Male","Item ID":47,"Item Name":"Alpha, Reach of Ending Hope","Price":1.55},{"SN":"Irillo49","Age":29,"Gender":"Male","Item ID":48,"Item Name":"Rage, Legacy of the Lone Victor","Price":4.32},{"SN":"Isri59","Age":35,"Gender":"Male","Item ID":73,"Item Name":"Ritual Mace","Price":3.74},{"SN":"Lisjaskan36","Age":25,"Gender":"Female","Item ID":88,"Item Name":"Emberling, Defender of Delusions","Price":4.1},{"SN":"Aiduecal76","Age":29,"Gender":"Male","Item ID":78,"Item Name":"Glimmer, Ender of the Moon","Price":2.33},{"SN":"Frichosiala98","Age":25,"Gender":"Male","Item ID":54,"Item Name":"Eternal Cleaver","Price":3.14},{"SN":"Deelilsasya30","Age":23,"Gender":"Male","Item ID":170,"Item Name":"Shadowsteel","Price":1.98},{"SN":"Mindilsa60","Age":23,"Gender":"Male","Item ID":99,"Item Name":"Expiration, Warscythe Of Lost Worlds","Price":4.53},{"SN":"Iladarla40","Age":8,"Gender":"Male","Item ID":79,"Item Name":"Alpha, Oath of Zeal","Price":2.88},{"SN":"Chrathybust28","Age":25,"Gender":"Male","Item ID":104,"Item Name":"Gladiator's Glaive","Price":1.36},{"SN":"Yarithsurgue62","Age":7,"Gender":"Male","Item ID":53,"Item Name":"Vengeance Cleaver","Price":3.7},{"SN":"Lisistaya47","Age":7,"Gender":"Male","Item ID":121,"Item Name":"Massacre","Price":3.42},{"SN":"Mindossa76","Age":21,"Gender":"Male","Item ID":95,"Item Name":"Singed Onyx Warscythe","Price":1.03},{"SN":"Assilsan72","Age":20,"Gender":"Male","Item ID":64,"Item Name":"Fusion Pummel","Price":3.58},{"SN":"Frichosiala98","Age":25,"Gender":"Male","Item ID":135,"Item Name":"Warped Diamond Crusader","Price":4.66},{"SN":"Assassa43","Age":22,"Gender":"Male","Item ID":70,"Item Name":"Hope's End","Price":3.89},{"SN":"Yarolwen77","Age":24,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Faralcil63","Age":26,"Gender":"Other \/ Non-Disclosed","Item ID":141,"Item Name":"Persuasion","Price":3.27},{"SN":"Sondilsa40","Age":18,"Gender":"Male","Item ID":119,"Item Name":"Stormbringer, Dark Blade of Ending Misery","Price":2.32},{"SN":"Lisossan98","Age":15,"Gender":"Male","Item ID":99,"Item Name":"Expiration, Warscythe Of Lost Worlds","Price":4.53},{"SN":"Chadossa89","Age":22,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Eosrirgue62","Age":34,"Gender":"Male","Item ID":183,"Item Name":"Dragon's Greatsword","Price":2.36},{"SN":"Lassilsa41","Age":27,"Gender":"Female","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Sondastan54","Age":31,"Gender":"Male","Item ID":173,"Item Name":"Stormfury Longsword","Price":4.83},{"SN":"Filrion44","Age":22,"Gender":"Male","Item ID":98,"Item Name":"Deadline, Voice Of Subtlety","Price":3.62},{"SN":"Lassassasda30","Age":15,"Gender":"Male","Item ID":102,"Item Name":"Avenger","Price":4.16},{"SN":"Aidain51","Age":26,"Gender":"Male","Item ID":180,"Item Name":"Stormcaller","Price":2.78},{"SN":"Aduephos78","Age":37,"Gender":"Male","Item ID":79,"Item Name":"Alpha, Oath of Zeal","Price":2.88},{"SN":"Hainaria90","Age":21,"Gender":"Male","Item ID":108,"Item Name":"Extraction, Quickblade Of Trembling Hands","Price":3.39},{"SN":"Eusri70","Age":30,"Gender":"Male","Item ID":131,"Item Name":"Fury","Price":4.82},{"SN":"Raerithsti62","Age":18,"Gender":"Male","Item ID":115,"Item Name":"Spectral Diamond Doomblade","Price":4.25},{"SN":"Aerithllora36","Age":29,"Gender":"Male","Item ID":68,"Item Name":"Storm-Weaver, Slayer of Inception","Price":2.49},{"SN":"Reuthelis39","Age":20,"Gender":"Female","Item ID":33,"Item Name":"Curved Axe","Price":1.35},{"SN":"Sundaststa26","Age":22,"Gender":"Female","Item ID":145,"Item Name":"Fiery Glass Crusader","Price":4.45},{"SN":"Aelin32","Age":24,"Gender":"Male","Item ID":54,"Item Name":"Eternal Cleaver","Price":3.14},{"SN":"Sundadarla27","Age":20,"Gender":"Male","Item ID":12,"Item Name":"Dawne","Price":4.3},{"SN":"Aeliru63","Age":22,"Gender":"Male","Item ID":173,"Item Name":"Stormfury Longsword","Price":4.83},{"SN":"Mindilsa60","Age":23,"Gender":"Male","Item ID":60,"Item Name":"Wolf","Price":1.84},{"SN":"Lisista27","Age":42,"Gender":"Male","Item ID":110,"Item Name":"Suspension","Price":2.11},{"SN":"Narirra38","Age":23,"Gender":"Female","Item ID":76,"Item Name":"Haunted Bronzed Bludgeon","Price":4.12},{"SN":"Eustyria89","Age":18,"Gender":"Male","Item ID":137,"Item Name":"Aetherius, Boon of the Blessed","Price":4.75},{"SN":"Phistym51","Age":22,"Gender":"Male","Item ID":29,"Item Name":"Chaos, Ender of the End","Price":3.79},{"SN":"Salilis27","Age":23,"Gender":"Female","Item ID":130,"Item Name":"Alpha","Price":1.56},{"SN":"Layjask75","Age":27,"Gender":"Male","Item ID":102,"Item Name":"Avenger","Price":4.16},{"SN":"Tyaeristi78","Age":24,"Gender":"Female","Item ID":47,"Item Name":"Alpha, Reach of Ending Hope","Price":1.55},{"SN":"Lirtyrdesta65","Age":19,"Gender":"Male","Item ID":60,"Item Name":"Wolf","Price":1.84},{"SN":"Syalollorap93","Age":20,"Gender":"Male","Item ID":7,"Item Name":"Thorn, Satchel of Dark Souls","Price":4.51},{"SN":"Assylla81","Age":22,"Gender":"Male","Item ID":125,"Item Name":"Whistling Mithril Warblade","Price":4.32},{"SN":"Eurisuru25","Age":27,"Gender":"Other \/ Non-Disclosed","Item ID":61,"Item Name":"Ragnarok","Price":3.97},{"SN":"Narirra38","Age":23,"Gender":"Female","Item ID":12,"Item Name":"Dawne","Price":4.3},{"SN":"Mindjasksya61","Age":20,"Gender":"Male","Item ID":70,"Item Name":"Hope's End","Price":3.89},{"SN":"Eusri44","Age":21,"Gender":"Male","Item ID":50,"Item Name":"Dawn","Price":2.55},{"SN":"Aeliru63","Age":22,"Gender":"Male","Item ID":30,"Item Name":"Stormcaller","Price":4.15},{"SN":"Rarith48","Age":20,"Gender":"Male","Item ID":15,"Item Name":"Soul Infused Crystal","Price":1.03},{"SN":"Yalaeria91","Age":16,"Gender":"Male","Item ID":179,"Item Name":"Wolf, Promise of the Moonwalker","Price":1.88},{"SN":"Iskadarya95","Age":15,"Gender":"Male","Item ID":173,"Item Name":"Stormfury Longsword","Price":4.83},{"SN":"Saedue76","Age":25,"Gender":"Male","Item ID":140,"Item Name":"Striker","Price":3.82},{"SN":"Lisossanya98","Age":17,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Iarithdil76","Age":20,"Gender":"Male","Item ID":57,"Item Name":"Despair, Favor of Due Diligence","Price":3.81},{"SN":"Chanosia60","Age":16,"Gender":"Male","Item ID":169,"Item Name":"Interrogator, Blood Blade of the Queen","Price":3.32},{"SN":"Aeliriarin93","Age":20,"Gender":"Male","Item ID":9,"Item Name":"Thorn, Conqueror of the Corrupted","Price":2.04},{"SN":"Raedalis34","Age":15,"Gender":"Female","Item ID":50,"Item Name":"Dawn","Price":2.55},{"SN":"Meosridil82","Age":15,"Gender":"Male","Item ID":33,"Item Name":"Curved Axe","Price":1.35},{"SN":"Sondossa55","Age":12,"Gender":"Male","Item ID":66,"Item Name":"Victor Iron Spikes","Price":3.55},{"SN":"Iadueria43","Age":22,"Gender":"Male","Item ID":15,"Item Name":"Soul Infused Crystal","Price":1.03},{"SN":"Lisico81","Age":17,"Gender":"Male","Item ID":14,"Item Name":"Possessed Core","Price":1.59},{"SN":"Ialo60","Age":24,"Gender":"Male","Item ID":146,"Item Name":"Warped Iron Scimitar","Price":4.08},{"SN":"Syathe73","Age":22,"Gender":"Male","Item ID":177,"Item Name":"Winterthorn, Defender of Shifting Worlds","Price":4.89},{"SN":"Lisassa26","Age":33,"Gender":"Male","Item ID":166,"Item Name":"Thirsty Iron Reaver","Price":4.25},{"SN":"Rasrirgue43","Age":21,"Gender":"Male","Item ID":93,"Item Name":"Apocalyptic Battlescythe","Price":3.91},{"SN":"Aerillorin70","Age":25,"Gender":"Male","Item ID":179,"Item Name":"Wolf, Promise of the Moonwalker","Price":1.88},{"SN":"Quelatarn54","Age":22,"Gender":"Male","Item ID":56,"Item Name":"Foul Titanium Battle Axe","Price":4.33},{"SN":"Airithrin43","Age":31,"Gender":"Female","Item ID":22,"Item Name":"Amnesia","Price":3.57},{"SN":"Mindirra92","Age":20,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Lisjasksda68","Age":26,"Gender":"Female","Item ID":85,"Item Name":"Malificent Bag","Price":2.17},{"SN":"Aerithnuphos61","Age":25,"Gender":"Male","Item ID":172,"Item Name":"Blade of the Grave","Price":1.69},{"SN":"Sundast29","Age":40,"Gender":"Male","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Lirtosia72","Age":14,"Gender":"Male","Item ID":87,"Item Name":"Deluge, Edge of the West","Price":2.2},{"SN":"Aeliriam77","Age":20,"Gender":"Male","Item ID":32,"Item Name":"Orenmir","Price":4.95},{"SN":"Lisirra55","Age":7,"Gender":"Female","Item ID":21,"Item Name":"Souleater","Price":3.27},{"SN":"Aeral97","Age":14,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Lisosiast26","Age":36,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Yathecal72","Age":32,"Gender":"Male","Item ID":16,"Item Name":"Restored Bauble","Price":3.11},{"SN":"Lirtistasta79","Age":23,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Lisadar44","Age":31,"Gender":"Male","Item ID":67,"Item Name":"Celeste, Incarnation of the Corrupted","Price":2.31},{"SN":"Jiskossa51","Age":23,"Gender":"Male","Item ID":133,"Item Name":"Faith's Scimitar","Price":3.82},{"SN":"Qilatie51","Age":20,"Gender":"Male","Item ID":100,"Item Name":"Blindscythe","Price":3.66},{"SN":"Eusri70","Age":30,"Gender":"Male","Item ID":153,"Item Name":"Mercenary Sabre","Price":4.57},{"SN":"Isurria36","Age":18,"Gender":"Female","Item ID":118,"Item Name":"Ghost Reaver, Longsword of Magic","Price":2.77},{"SN":"Sundastnya66","Age":7,"Gender":"Male","Item ID":151,"Item Name":"Severance","Price":1.85},{"SN":"Raesursurap33","Age":20,"Gender":"Male","Item ID":81,"Item Name":"Dreamkiss","Price":4.06},{"SN":"Sondassasya91","Age":23,"Gender":"Male","Item ID":94,"Item Name":"Mourning Blade","Price":1.82},{"SN":"Ermol76","Age":23,"Gender":"Male","Item ID":114,"Item Name":"Yearning Mageblade","Price":1.79},{"SN":"Eosurdru76","Age":7,"Gender":"Female","Item ID":77,"Item Name":"Piety, Guardian of Riddles","Price":3.68},{"SN":"Yadaisuir65","Age":22,"Gender":"Male","Item ID":42,"Item Name":"The Decapitator","Price":4.82},{"SN":"Zhisrisu83","Age":17,"Gender":"Male","Item ID":33,"Item Name":"Curved Axe","Price":1.35},{"SN":"Aduephos78","Age":37,"Gender":"Male","Item ID":174,"Item Name":"Primitive Blade","Price":2.46},{"SN":"Sondassa68","Age":30,"Gender":"Male","Item ID":69,"Item Name":"Frenzy, Defender of the Harvest","Price":1.06},{"SN":"Chamirraya83","Age":20,"Gender":"Male","Item ID":141,"Item Name":"Persuasion","Price":3.27},{"SN":"Alaephos75","Age":22,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Haellysu29","Age":21,"Gender":"Male","Item ID":166,"Item Name":"Thirsty Iron Reaver","Price":4.25},{"SN":"Yarithphos28","Age":25,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Ingatcil75","Age":7,"Gender":"Male","Item ID":66,"Item Name":"Victor Iron Spikes","Price":3.55},{"SN":"Eothe56","Age":30,"Gender":"Male","Item ID":143,"Item Name":"Frenzied Scimitar","Price":2.6},{"SN":"Haerith37","Age":25,"Gender":"Male","Item ID":158,"Item Name":"Darkheart, Butcher of the Champion","Price":3.56},{"SN":"Assithasta65","Age":23,"Gender":"Male","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61},{"SN":"Ethruard50","Age":24,"Gender":"Female","Item ID":51,"Item Name":"Endbringer","Price":2.67},{"SN":"Palurrian69","Age":15,"Gender":"Male","Item ID":32,"Item Name":"Orenmir","Price":4.95},{"SN":"Iskistasda86","Age":37,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Tyaili86","Age":17,"Gender":"Female","Item ID":86,"Item Name":"Stormfury Lantern","Price":1.28},{"SN":"Liawista80","Age":32,"Gender":"Male","Item ID":141,"Item Name":"Persuasion","Price":3.27},{"SN":"Seosri62","Age":35,"Gender":"Male","Item ID":159,"Item Name":"Oathbreaker, Spellblade of Trials","Price":3.01},{"SN":"Silinu63","Age":9,"Gender":"Male","Item ID":16,"Item Name":"Restored Bauble","Price":3.11},{"SN":"Aela49","Age":25,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Assosiasta83","Age":20,"Gender":"Male","Item ID":38,"Item Name":"The Void, Vengeance of Dark Magic","Price":2.82},{"SN":"Saelollop56","Age":40,"Gender":"Female","Item ID":77,"Item Name":"Piety, Guardian of Riddles","Price":3.68},{"SN":"Saena74","Age":35,"Gender":"Female","Item ID":108,"Item Name":"Extraction, Quickblade Of Trembling Hands","Price":3.39},{"SN":"Tyaelistidru84","Age":25,"Gender":"Female","Item ID":96,"Item Name":"Blood-Forged Skeletal Spine","Price":4.77},{"SN":"Chamirrasya33","Age":20,"Gender":"Male","Item ID":82,"Item Name":"Nirvana","Price":1.11},{"SN":"Smecherdi88","Age":15,"Gender":"Male","Item ID":27,"Item Name":"Riddle, Tribute of Ended Dreams","Price":3.96},{"SN":"Leulaesti78","Age":17,"Gender":"Male","Item ID":121,"Item Name":"Massacre","Price":3.42},{"SN":"Tyaenasti87","Age":8,"Gender":"Male","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Sondassa48","Age":22,"Gender":"Male","Item ID":113,"Item Name":"Solitude's Reaver","Price":2.67},{"SN":"Deural48","Age":11,"Gender":"Female","Item ID":46,"Item Name":"Hopeless Ebon Dualblade","Price":4.75},{"SN":"Saistydru69","Age":22,"Gender":"Male","Item ID":76,"Item Name":"Haunted Bronzed Bludgeon","Price":4.12},{"SN":"Chamosia29","Age":24,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Saisrilis27","Age":21,"Gender":"Male","Item ID":108,"Item Name":"Extraction, Quickblade Of Trembling Hands","Price":3.39},{"SN":"Indonmol95","Age":15,"Gender":"Male","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Fironon91","Age":20,"Gender":"Female","Item ID":45,"Item Name":"Glinting Glass Edge","Price":2.46},{"SN":"Ryanara76","Age":23,"Gender":"Male","Item ID":27,"Item Name":"Riddle, Tribute of Ended Dreams","Price":3.96},{"SN":"Saedue76","Age":25,"Gender":"Male","Item ID":7,"Item Name":"Thorn, Satchel of Dark Souls","Price":4.51},{"SN":"Lirtossanya27","Age":24,"Gender":"Female","Item ID":114,"Item Name":"Yearning Mageblade","Price":1.79},{"SN":"Sondadar26","Age":24,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Phalinun47","Age":15,"Gender":"Male","Item ID":10,"Item Name":"Sleepwalker","Price":1.73},{"SN":"Chamistast30","Age":25,"Gender":"Female","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Hiarideu73","Age":25,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Qilunan34","Age":16,"Gender":"Male","Item ID":119,"Item Name":"Stormbringer, Dark Blade of Ending Misery","Price":2.32},{"SN":"Pharithdil38","Age":21,"Gender":"Male","Item ID":66,"Item Name":"Victor Iron Spikes","Price":3.55},{"SN":"Tyeuladeu30","Age":25,"Gender":"Female","Item ID":42,"Item Name":"The Decapitator","Price":4.82},{"SN":"Sondastan54","Age":31,"Gender":"Male","Item ID":170,"Item Name":"Shadowsteel","Price":1.98},{"SN":"Ina92","Age":22,"Gender":"Male","Item ID":150,"Item Name":"Deathraze","Price":4.54},{"SN":"Saida58","Age":24,"Gender":"Male","Item ID":164,"Item Name":"Exiled Doomblade","Price":1.92},{"SN":"Aithelis62","Age":32,"Gender":"Other \/ Non-Disclosed","Item ID":29,"Item Name":"Chaos, Ender of the End","Price":3.79},{"SN":"Indcil77","Age":40,"Gender":"Male","Item ID":139,"Item Name":"Mercy, Katana of Dismay","Price":4.37},{"SN":"Hallysucal81","Age":20,"Gender":"Male","Item ID":14,"Item Name":"Possessed Core","Price":1.59},{"SN":"Tyeuduephos81","Age":15,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Heosrisuir72","Age":19,"Gender":"Male","Item ID":131,"Item Name":"Fury","Price":4.82},{"SN":"Chadossa56","Age":37,"Gender":"Female","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Hailaphos89","Age":20,"Gender":"Male","Item ID":82,"Item Name":"Nirvana","Price":1.11},{"SN":"Lirtassa47","Age":27,"Gender":"Male","Item ID":74,"Item Name":"Yearning Crusher","Price":1.06},{"SN":"Aduephos78","Age":37,"Gender":"Male","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Sondilsa40","Age":18,"Gender":"Male","Item ID":20,"Item Name":"Netherbane","Price":1.48},{"SN":"Ithesuphos68","Age":23,"Gender":"Male","Item ID":180,"Item Name":"Stormcaller","Price":2.78},{"SN":"Eula35","Age":25,"Gender":"Male","Item ID":98,"Item Name":"Deadline, Voice Of Subtlety","Price":3.62},{"SN":"Aina42","Age":27,"Gender":"Female","Item ID":159,"Item Name":"Oathbreaker, Spellblade of Trials","Price":3.01},{"SN":"Ethrusuard41","Age":10,"Gender":"Male","Item ID":131,"Item Name":"Fury","Price":4.82},{"SN":"Zhisrisu83","Age":17,"Gender":"Male","Item ID":82,"Item Name":"Nirvana","Price":1.11},{"SN":"Isursti83","Age":24,"Gender":"Male","Item ID":111,"Item Name":"Misery's End","Price":2.91},{"SN":"Chanirrasta87","Age":19,"Gender":"Male","Item ID":41,"Item Name":"Orbit","Price":1.16},{"SN":"Stryanastip77","Age":21,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Ilirrasda54","Age":22,"Gender":"Male","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61},{"SN":"Liri91","Age":7,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Undadar97","Age":25,"Gender":"Male","Item ID":8,"Item Name":"Purgatory, Gem of Regret","Price":3.91},{"SN":"Ithergue48","Age":20,"Gender":"Female","Item ID":179,"Item Name":"Wolf, Promise of the Moonwalker","Price":1.88},{"SN":"Saistyphos30","Age":32,"Gender":"Female","Item ID":95,"Item Name":"Singed Onyx Warscythe","Price":1.03},{"SN":"Lisosianya62","Age":22,"Gender":"Male","Item ID":47,"Item Name":"Alpha, Reach of Ending Hope","Price":1.55},{"SN":"Tyaelistidru84","Age":25,"Gender":"Female","Item ID":6,"Item Name":"Rusty Skull","Price":1.2},{"SN":"Sausosia74","Age":25,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Frichosiala98","Age":25,"Gender":"Male","Item ID":123,"Item Name":"Twilight's Carver","Price":1.14},{"SN":"Mindimnya67","Age":39,"Gender":"Female","Item ID":140,"Item Name":"Striker","Price":3.82},{"SN":"Undistasta86","Age":12,"Gender":"Male","Item ID":163,"Item Name":"Thunderfury Scimitar","Price":3.02},{"SN":"Lirtistasta79","Age":23,"Gender":"Male","Item ID":172,"Item Name":"Blade of the Grave","Price":1.69},{"SN":"Alaesu91","Age":18,"Gender":"Female","Item ID":95,"Item Name":"Singed Onyx Warscythe","Price":1.03},{"SN":"Jiskosiala43","Age":9,"Gender":"Female","Item ID":100,"Item Name":"Blindscythe","Price":3.66},{"SN":"Heuralsti66","Age":30,"Gender":"Male","Item ID":137,"Item Name":"Aetherius, Boon of the Blessed","Price":4.75},{"SN":"Umuard36","Age":23,"Gender":"Female","Item ID":66,"Item Name":"Victor Iron Spikes","Price":3.55},{"SN":"Asur53","Age":29,"Gender":"Male","Item ID":68,"Item Name":"Storm-Weaver, Slayer of Inception","Price":2.49},{"SN":"Jiskassa76","Age":25,"Gender":"Male","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Thryallym62","Age":20,"Gender":"Male","Item ID":124,"Item Name":"Venom Claymore","Price":2.72},{"SN":"Raesty92","Age":25,"Gender":"Male","Item ID":5,"Item Name":"Putrid Fan","Price":1.32},{"SN":"Frichassala85","Age":21,"Gender":"Male","Item ID":69,"Item Name":"Frenzy, Defender of the Harvest","Price":1.06},{"SN":"Chamilsan75","Age":24,"Gender":"Female","Item ID":90,"Item Name":"Betrayer","Price":1.67},{"SN":"Ilosu82","Age":33,"Gender":"Male","Item ID":38,"Item Name":"The Void, Vengeance of Dark Magic","Price":2.82},{"SN":"Mindimnya67","Age":39,"Gender":"Female","Item ID":163,"Item Name":"Thunderfury Scimitar","Price":3.02},{"SN":"Pheodai94","Age":23,"Gender":"Male","Item ID":20,"Item Name":"Netherbane","Price":1.48},{"SN":"Raerithsti62","Age":18,"Gender":"Male","Item ID":11,"Item Name":"Brimstone","Price":2.52},{"SN":"Undirrasta74","Age":22,"Gender":"Male","Item ID":41,"Item Name":"Orbit","Price":1.16},{"SN":"Hiasur92","Age":25,"Gender":"Female","Item ID":103,"Item Name":"Singed Scalpel","Price":4.87},{"SN":"Tillyrin30","Age":20,"Gender":"Male","Item ID":19,"Item Name":"Pursuit, Cudgel of Necromancy","Price":3.98},{"SN":"Riralsti91","Age":24,"Gender":"Male","Item ID":134,"Item Name":"Undead Crusader","Price":4.67},{"SN":"Iasur80","Age":24,"Gender":"Male","Item ID":103,"Item Name":"Singed Scalpel","Price":4.87},{"SN":"Eryon48","Age":15,"Gender":"Female","Item ID":110,"Item Name":"Suspension","Price":2.11},{"SN":"Whaestysu86","Age":22,"Gender":"Male","Item ID":146,"Item Name":"Warped Iron Scimitar","Price":4.08},{"SN":"Aiduesu83","Age":29,"Gender":"Female","Item ID":35,"Item Name":"Heartless Bone Dualblade","Price":2.63},{"SN":"Iaralsuir44","Age":22,"Gender":"Male","Item ID":105,"Item Name":"Hailstorm Shadowsteel Scythe","Price":3.73},{"SN":"Chanjask65","Age":36,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Frichistast39","Age":25,"Gender":"Male","Item ID":158,"Item Name":"Darkheart, Butcher of the Champion","Price":3.56},{"SN":"Yaralnura48","Age":40,"Gender":"Male","Item ID":168,"Item Name":"Sun Strike, Jaws of Twisted Visions","Price":2.64},{"SN":"Isursti83","Age":24,"Gender":"Male","Item ID":48,"Item Name":"Rage, Legacy of the Lone Victor","Price":4.32},{"SN":"Phairinum94","Age":17,"Gender":"Male","Item ID":128,"Item Name":"Blazeguard, Reach of Eternity","Price":4.0},{"SN":"Ethralan59","Age":27,"Gender":"Male","Item ID":151,"Item Name":"Severance","Price":1.85},{"SN":"Raelly43","Age":25,"Gender":"Male","Item ID":165,"Item Name":"Bone Crushing Silver Skewer","Price":3.37},{"SN":"Lisassasta50","Age":33,"Gender":"Female","Item ID":22,"Item Name":"Amnesia","Price":3.57},{"SN":"Chanastnya43","Age":25,"Gender":"Female","Item ID":104,"Item Name":"Gladiator's Glaive","Price":1.36},{"SN":"Sondimla25","Age":23,"Gender":"Male","Item ID":85,"Item Name":"Malificent Bag","Price":2.17},{"SN":"Chamilsala65","Age":24,"Gender":"Male","Item ID":136,"Item Name":"Ghastly Adamantite Protector","Price":3.3},{"SN":"Idaria87","Age":30,"Gender":"Male","Item ID":103,"Item Name":"Singed Scalpel","Price":4.87},{"SN":"Eoda93","Age":22,"Gender":"Male","Item ID":76,"Item Name":"Haunted Bronzed Bludgeon","Price":4.12},{"SN":"Chanastst38","Age":27,"Gender":"Male","Item ID":21,"Item Name":"Souleater","Price":3.27},{"SN":"Lamil79","Age":23,"Gender":"Male","Item ID":40,"Item Name":"Second Chance","Price":2.34},{"SN":"Liri91","Age":7,"Gender":"Male","Item ID":161,"Item Name":"Devine","Price":1.45},{"SN":"Qaronon57","Age":17,"Gender":"Male","Item ID":22,"Item Name":"Amnesia","Price":3.57},{"SN":"Chadjask77","Age":36,"Gender":"Male","Item ID":57,"Item Name":"Despair, Favor of Due Diligence","Price":3.81},{"SN":"Ethralista69","Age":20,"Gender":"Male","Item ID":52,"Item Name":"Hatred","Price":4.39},{"SN":"Phaeduesurgue38","Age":23,"Gender":"Male","Item ID":49,"Item Name":"The Oculus, Token of Lost Worlds","Price":4.23},{"SN":"Rathellorin54","Age":25,"Gender":"Female","Item ID":95,"Item Name":"Singed Onyx Warscythe","Price":1.03},{"SN":"Filon68","Age":38,"Gender":"Male","Item ID":40,"Item Name":"Second Chance","Price":2.34},{"SN":"Chamilsala65","Age":24,"Gender":"Male","Item ID":160,"Item Name":"Azurewrath","Price":2.22},{"SN":"Assylla81","Age":22,"Gender":"Male","Item ID":1,"Item Name":"Crucifer","Price":2.28},{"SN":"Ingonon91","Age":21,"Gender":"Male","Item ID":79,"Item Name":"Alpha, Oath of Zeal","Price":2.88},{"SN":"Lisovynya38","Age":18,"Gender":"Male","Item ID":144,"Item Name":"Blood Infused Guardian","Price":2.86},{"SN":"Assesi91","Age":25,"Gender":"Male","Item ID":10,"Item Name":"Sleepwalker","Price":1.73},{"SN":"Aellyria80","Age":25,"Gender":"Male","Item ID":125,"Item Name":"Whistling Mithril Warblade","Price":4.32},{"SN":"Aethedru70","Age":25,"Gender":"Male","Item ID":176,"Item Name":"Relentless Iron Skewer","Price":2.97},{"SN":"Iladarla40","Age":8,"Gender":"Male","Item ID":15,"Item Name":"Soul Infused Crystal","Price":1.03},{"SN":"Tyalaesu89","Age":29,"Gender":"Male","Item ID":180,"Item Name":"Stormcaller","Price":2.78},{"SN":"Erudrion71","Age":16,"Gender":"Male","Item ID":161,"Item Name":"Devine","Price":1.45},{"SN":"Tyisriphos58","Age":38,"Gender":"Male","Item ID":181,"Item Name":"Reaper's Toll","Price":4.56},{"SN":"Iskista88","Age":28,"Gender":"Male","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Seudaillorap38","Age":21,"Gender":"Male","Item ID":133,"Item Name":"Faith's Scimitar","Price":3.82},{"SN":"Sondossa55","Age":12,"Gender":"Male","Item ID":70,"Item Name":"Hope's End","Price":3.89},{"SN":"Tyirithnu40","Age":19,"Gender":"Male","Item ID":108,"Item Name":"Extraction, Quickblade Of Trembling Hands","Price":3.39},{"SN":"Malista67","Age":13,"Gender":"Male","Item ID":159,"Item Name":"Oathbreaker, Spellblade of Trials","Price":3.01},{"SN":"Ristydru66","Age":33,"Gender":"Male","Item ID":120,"Item Name":"Agatha","Price":1.91},{"SN":"Yasriphos60","Age":40,"Gender":"Male","Item ID":11,"Item Name":"Brimstone","Price":2.52},{"SN":"Phainasu47","Age":20,"Gender":"Male","Item ID":111,"Item Name":"Misery's End","Price":2.91},{"SN":"Eural50","Age":22,"Gender":"Male","Item ID":81,"Item Name":"Dreamkiss","Price":4.06},{"SN":"Mindassast27","Age":22,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Iskossan49","Age":24,"Gender":"Male","Item ID":62,"Item Name":"Piece Maker","Price":4.36},{"SN":"Qarrian82","Age":30,"Gender":"Male","Item ID":145,"Item Name":"Fiery Glass Crusader","Price":4.45},{"SN":"Eulidru49","Age":16,"Gender":"Female","Item ID":170,"Item Name":"Shadowsteel","Price":1.98},{"SN":"Inguard95","Age":38,"Gender":"Male","Item ID":148,"Item Name":"Warmonger, Gift of Suffering's End","Price":3.96},{"SN":"Hiral75","Age":20,"Gender":"Male","Item ID":161,"Item Name":"Devine","Price":1.45},{"SN":"Undast38","Age":16,"Gender":"Male","Item ID":162,"Item Name":"Abyssal Shard","Price":2.04},{"SN":"Chadjask77","Age":36,"Gender":"Male","Item ID":182,"Item Name":"Toothpick","Price":3.48},{"SN":"Marim28","Age":17,"Gender":"Female","Item ID":143,"Item Name":"Frenzied Scimitar","Price":2.6},{"SN":"Yasriphos60","Age":40,"Gender":"Male","Item ID":55,"Item Name":"Vindictive Glass Edge","Price":4.26},{"SN":"Ialistidru50","Age":21,"Gender":"Male","Item ID":22,"Item Name":"Amnesia","Price":3.57},{"SN":"Aelalis34","Age":38,"Gender":"Male","Item ID":172,"Item Name":"Blade of the Grave","Price":1.69},{"SN":"Airal46","Age":35,"Gender":"Male","Item ID":113,"Item Name":"Solitude's Reaver","Price":2.67},{"SN":"Lirtosia72","Age":14,"Gender":"Male","Item ID":80,"Item Name":"Dreamsong","Price":3.81},{"SN":"Assassasta79","Age":17,"Gender":"Female","Item ID":177,"Item Name":"Winterthorn, Defender of Shifting Worlds","Price":4.89},{"SN":"Saerallora71","Age":21,"Gender":"Male","Item ID":183,"Item Name":"Dragon's Greatsword","Price":2.36},{"SN":"Frichossast86","Age":24,"Gender":"Male","Item ID":98,"Item Name":"Deadline, Voice Of Subtlety","Price":3.62},{"SN":"Undirra73","Age":23,"Gender":"Female","Item ID":30,"Item Name":"Stormcaller","Price":4.15},{"SN":"Chanastsda67","Age":15,"Gender":"Male","Item ID":145,"Item Name":"Fiery Glass Crusader","Price":4.45},{"SN":"Undirrala66","Age":29,"Gender":"Male","Item ID":18,"Item Name":"Torchlight, Bond of Storms","Price":1.77},{"SN":"Lirtosia72","Age":14,"Gender":"Male","Item ID":183,"Item Name":"Dragon's Greatsword","Price":2.36},{"SN":"Phaestycal84","Age":31,"Gender":"Male","Item ID":171,"Item Name":"Scalpel","Price":3.62},{"SN":"Malunil62","Age":19,"Gender":"Male","Item ID":153,"Item Name":"Mercenary Sabre","Price":4.57},{"SN":"Eosursurap97","Age":20,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Iaralrgue74","Age":15,"Gender":"Male","Item ID":153,"Item Name":"Mercenary Sabre","Price":4.57},{"SN":"Seolollo93","Age":15,"Gender":"Male","Item ID":8,"Item Name":"Purgatory, Gem of Regret","Price":3.91},{"SN":"Ililsan66","Age":18,"Gender":"Male","Item ID":15,"Item Name":"Soul Infused Crystal","Price":1.03},{"SN":"Yasriphos60","Age":40,"Gender":"Male","Item ID":171,"Item Name":"Scalpel","Price":3.62},{"SN":"Iskosia51","Age":15,"Gender":"Male","Item ID":154,"Item Name":"Feral Katana","Price":2.19},{"SN":"Isurria36","Age":18,"Gender":"Female","Item ID":171,"Item Name":"Scalpel","Price":3.62},{"SN":"Asur53","Age":29,"Gender":"Male","Item ID":129,"Item Name":"Fate, Vengeance of Eternal Justice","Price":1.55},{"SN":"Aesur96","Age":34,"Gender":"Male","Item ID":135,"Item Name":"Warped Diamond Crusader","Price":4.66},{"SN":"Iskosian40","Age":23,"Gender":"Male","Item ID":108,"Item Name":"Extraction, Quickblade Of Trembling Hands","Price":3.39},{"SN":"Ililsa62","Age":20,"Gender":"Male","Item ID":100,"Item Name":"Blindscythe","Price":3.66},{"SN":"Aillyriadru65","Age":23,"Gender":"Male","Item ID":60,"Item Name":"Wolf","Price":1.84},{"SN":"Lisassa49","Age":24,"Gender":"Female","Item ID":110,"Item Name":"Suspension","Price":2.11},{"SN":"Lisistaya47","Age":7,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Ialidru40","Age":19,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Sondim43","Age":20,"Gender":"Male","Item ID":35,"Item Name":"Heartless Bone Dualblade","Price":2.63},{"SN":"Iskimnya76","Age":24,"Gender":"Male","Item ID":30,"Item Name":"Stormcaller","Price":4.15},{"SN":"Aethe80","Age":22,"Gender":"Male","Item ID":119,"Item Name":"Stormbringer, Dark Blade of Ending Misery","Price":2.32},{"SN":"Rathellorin54","Age":25,"Gender":"Female","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Chanadar44","Age":29,"Gender":"Male","Item ID":64,"Item Name":"Fusion Pummel","Price":3.58},{"SN":"Eudasu82","Age":33,"Gender":"Male","Item ID":83,"Item Name":"Lifebender","Price":3.51},{"SN":"Lisirraya76","Age":19,"Gender":"Male","Item ID":88,"Item Name":"Emberling, Defender of Delusions","Price":4.1},{"SN":"Lisossa25","Age":24,"Gender":"Male","Item ID":26,"Item Name":"Unholy Wand","Price":1.88},{"SN":"Haedasu65","Age":20,"Gender":"Male","Item ID":133,"Item Name":"Faith's Scimitar","Price":3.82},{"SN":"Iral74","Age":24,"Gender":"Male","Item ID":97,"Item Name":"Swan Song, Gouger Of Terror","Price":3.58},{"SN":"Lisjaskya84","Age":20,"Gender":"Male","Item ID":16,"Item Name":"Restored Bauble","Price":3.11},{"SN":"Saelaephos52","Age":20,"Gender":"Male","Item ID":181,"Item Name":"Reaper's Toll","Price":4.56},{"SN":"Chamim85","Age":22,"Gender":"Male","Item ID":76,"Item Name":"Haunted Bronzed Bludgeon","Price":4.12},{"SN":"Chamadar61","Age":21,"Gender":"Male","Item ID":154,"Item Name":"Feral Katana","Price":2.19},{"SN":"Lirtista72","Age":23,"Gender":"Male","Item ID":142,"Item Name":"Righteous Might","Price":4.36},{"SN":"Seudanu38","Age":17,"Gender":"Male","Item ID":113,"Item Name":"Solitude's Reaver","Price":2.67},{"SN":"Lisossa63","Age":24,"Gender":"Male","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Siathecal92","Age":22,"Gender":"Male","Item ID":36,"Item Name":"Spectral Bone Axe","Price":2.98},{"SN":"Eullydru35","Age":7,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Chamistast30","Age":25,"Gender":"Female","Item ID":18,"Item Name":"Torchlight, Bond of Storms","Price":1.77},{"SN":"Isrirgue68","Age":24,"Gender":"Male","Item ID":142,"Item Name":"Righteous Might","Price":4.36},{"SN":"Eurallo89","Age":20,"Gender":"Female","Item ID":172,"Item Name":"Blade of the Grave","Price":1.69},{"SN":"Raithe71","Age":25,"Gender":"Male","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61},{"SN":"Iskossaya95","Age":31,"Gender":"Male","Item ID":151,"Item Name":"Severance","Price":1.85},{"SN":"Yathecal82","Age":23,"Gender":"Male","Item ID":178,"Item Name":"Oathbreaker, Last Hope of the Breaking Storm","Price":2.41},{"SN":"Filrion44","Age":22,"Gender":"Male","Item ID":68,"Item Name":"Storm-Weaver, Slayer of Inception","Price":2.49},{"SN":"Saralp86","Age":9,"Gender":"Male","Item ID":26,"Item Name":"Unholy Wand","Price":1.88},{"SN":"Tyeuduen32","Age":22,"Gender":"Male","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Aina43","Age":21,"Gender":"Female","Item ID":174,"Item Name":"Primitive Blade","Price":2.46},{"SN":"Undiwinya88","Age":15,"Gender":"Male","Item ID":23,"Item Name":"Crucifer","Price":2.77},{"SN":"Silaera56","Age":29,"Gender":"Male","Item ID":75,"Item Name":"Brutality Ivory Warmace","Price":1.72},{"SN":"Iskadarya95","Age":15,"Gender":"Male","Item ID":27,"Item Name":"Riddle, Tribute of Ended Dreams","Price":3.96},{"SN":"Eoralphos86","Age":13,"Gender":"Female","Item ID":26,"Item Name":"Unholy Wand","Price":1.88},{"SN":"Billysu76","Age":27,"Gender":"Male","Item ID":144,"Item Name":"Blood Infused Guardian","Price":2.86},{"SN":"Seorithstilis90","Age":23,"Gender":"Male","Item ID":152,"Item Name":"Darkheart","Price":3.15},{"SN":"Aidaira48","Age":30,"Gender":"Male","Item ID":10,"Item Name":"Sleepwalker","Price":1.73},{"SN":"Mindimnya67","Age":39,"Gender":"Female","Item ID":145,"Item Name":"Fiery Glass Crusader","Price":4.45},{"SN":"Euna48","Age":22,"Gender":"Other \/ Non-Disclosed","Item ID":115,"Item Name":"Spectral Diamond Doomblade","Price":4.25},{"SN":"Lisassasta50","Age":33,"Gender":"Female","Item ID":163,"Item Name":"Thunderfury Scimitar","Price":3.02},{"SN":"Eusur90","Age":20,"Gender":"Male","Item ID":30,"Item Name":"Stormcaller","Price":4.15},{"SN":"Undirrala66","Age":29,"Gender":"Male","Item ID":133,"Item Name":"Faith's Scimitar","Price":3.82},{"SN":"Lamil70","Age":16,"Gender":"Male","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Chamadarnya73","Age":21,"Gender":"Male","Item ID":12,"Item Name":"Dawne","Price":4.3},{"SN":"Ilast79","Age":20,"Gender":"Female","Item ID":6,"Item Name":"Rusty Skull","Price":1.2},{"SN":"Sondilsa35","Age":22,"Gender":"Male","Item ID":97,"Item Name":"Swan Song, Gouger Of Terror","Price":3.58},{"SN":"Ralonurin90","Age":26,"Gender":"Male","Item ID":148,"Item Name":"Warmonger, Gift of Suffering's End","Price":3.96},{"SN":"Marundi65","Age":24,"Gender":"Female","Item ID":71,"Item Name":"Demise","Price":4.07},{"SN":"Phaedan76","Age":20,"Gender":"Male","Item ID":60,"Item Name":"Wolf","Price":1.84},{"SN":"Farenon57","Age":20,"Gender":"Male","Item ID":18,"Item Name":"Torchlight, Bond of Storms","Price":1.77},{"SN":"Ilassa51","Age":20,"Gender":"Male","Item ID":157,"Item Name":"Spada, Etcher of Hatred","Price":2.21},{"SN":"Lirtossa84","Age":20,"Gender":"Male","Item ID":101,"Item Name":"Final Critic","Price":4.62},{"SN":"Airi27","Age":23,"Gender":"Male","Item ID":38,"Item Name":"The Void, Vengeance of Dark Magic","Price":2.82},{"SN":"Indcil77","Age":40,"Gender":"Male","Item ID":102,"Item Name":"Avenger","Price":4.16},{"SN":"Chamastya76","Age":20,"Gender":"Male","Item ID":53,"Item Name":"Vengeance Cleaver","Price":3.7},{"SN":"Lassjask63","Age":7,"Gender":"Male","Item ID":158,"Item Name":"Darkheart, Butcher of the Champion","Price":3.56},{"SN":"Heolo60","Age":22,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Isurria36","Age":18,"Gender":"Female","Item ID":101,"Item Name":"Final Critic","Price":4.62},{"SN":"Lisossan98","Age":15,"Gender":"Male","Item ID":153,"Item Name":"Mercenary Sabre","Price":4.57},{"SN":"Sondim43","Age":20,"Gender":"Male","Item ID":19,"Item Name":"Pursuit, Cudgel of Necromancy","Price":3.98},{"SN":"Mindirra92","Age":20,"Gender":"Male","Item ID":11,"Item Name":"Brimstone","Price":2.52},{"SN":"Reuthelis39","Age":20,"Gender":"Female","Item ID":11,"Item Name":"Brimstone","Price":2.52},{"SN":"Thourdirra92","Age":18,"Gender":"Male","Item ID":166,"Item Name":"Thirsty Iron Reaver","Price":4.25},{"SN":"Frichadar89","Age":25,"Gender":"Male","Item ID":49,"Item Name":"The Oculus, Token of Lost Worlds","Price":4.23},{"SN":"Raesursurap33","Age":20,"Gender":"Male","Item ID":123,"Item Name":"Twilight's Carver","Price":1.14},{"SN":"Jiskilsa35","Age":20,"Gender":"Female","Item ID":80,"Item Name":"Dreamsong","Price":3.81},{"SN":"Philistirap41","Age":33,"Gender":"Male","Item ID":172,"Item Name":"Blade of the Grave","Price":1.69},{"SN":"Tyidainu31","Age":20,"Gender":"Male","Item ID":144,"Item Name":"Blood Infused Guardian","Price":2.86},{"SN":"Mindimnya67","Age":39,"Gender":"Female","Item ID":161,"Item Name":"Devine","Price":1.45},{"SN":"Tridaira71","Age":37,"Gender":"Female","Item ID":95,"Item Name":"Singed Onyx Warscythe","Price":1.03},{"SN":"Queusurra38","Age":23,"Gender":"Male","Item ID":90,"Item Name":"Betrayer","Price":1.67},{"SN":"Mindadaran26","Age":20,"Gender":"Male","Item ID":124,"Item Name":"Venom Claymore","Price":2.72},{"SN":"Lisassa39","Age":23,"Gender":"Male","Item ID":130,"Item Name":"Alpha","Price":1.56},{"SN":"Alaesu77","Age":32,"Gender":"Male","Item ID":78,"Item Name":"Glimmer, Ender of the Moon","Price":2.33},{"SN":"Ilogha82","Age":25,"Gender":"Male","Item ID":142,"Item Name":"Righteous Might","Price":4.36},{"SN":"Pharithdil38","Age":21,"Gender":"Male","Item ID":178,"Item Name":"Oathbreaker, Last Hope of the Breaking Storm","Price":2.41},{"SN":"Mindossasya74","Age":26,"Gender":"Male","Item ID":85,"Item Name":"Malificent Bag","Price":2.17},{"SN":"Syadaillo88","Age":16,"Gender":"Male","Item ID":22,"Item Name":"Amnesia","Price":3.57},{"SN":"Lassilsala30","Age":15,"Gender":"Male","Item ID":127,"Item Name":"Heartseeker, Reaver of Souls","Price":3.21},{"SN":"Eusri26","Age":23,"Gender":"Male","Item ID":111,"Item Name":"Misery's End","Price":2.91},{"SN":"Chanastsda67","Age":15,"Gender":"Male","Item ID":67,"Item Name":"Celeste, Incarnation of the Corrupted","Price":2.31},{"SN":"Hilaerin92","Age":31,"Gender":"Male","Item ID":40,"Item Name":"Second Chance","Price":2.34},{"SN":"Aeliriam77","Age":20,"Gender":"Male","Item ID":18,"Item Name":"Torchlight, Bond of Storms","Price":1.77},{"SN":"Lirtossan50","Age":35,"Gender":"Male","Item ID":83,"Item Name":"Lifebender","Price":3.51},{"SN":"Iskossan49","Age":24,"Gender":"Male","Item ID":94,"Item Name":"Mourning Blade","Price":1.82},{"SN":"Sondim73","Age":16,"Gender":"Male","Item ID":22,"Item Name":"Amnesia","Price":3.57},{"SN":"Assosia38","Age":16,"Gender":"Male","Item ID":37,"Item Name":"Shadow Strike, Glory of Ending Hope","Price":1.93},{"SN":"Reula64","Age":16,"Gender":"Male","Item ID":115,"Item Name":"Spectral Diamond Doomblade","Price":4.25},{"SN":"Tyeosri53","Age":31,"Gender":"Male","Item ID":182,"Item Name":"Toothpick","Price":3.48},{"SN":"Raesurdil91","Age":43,"Gender":"Male","Item ID":57,"Item Name":"Despair, Favor of Due Diligence","Price":3.81},{"SN":"Anallorgue57","Age":20,"Gender":"Female","Item ID":103,"Item Name":"Singed Scalpel","Price":4.87},{"SN":"Idai61","Age":21,"Gender":"Male","Item ID":78,"Item Name":"Glimmer, Ender of the Moon","Price":2.33},{"SN":"Aeduera68","Age":26,"Gender":"Male","Item ID":156,"Item Name":"Soul-Forged Steel Shortsword","Price":1.16},{"SN":"Rithe53","Age":23,"Gender":"Male","Item ID":92,"Item Name":"Final Critic","Price":1.36},{"SN":"Quinarap53","Age":21,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Haerithp41","Age":24,"Gender":"Male","Item ID":109,"Item Name":"Downfall, Scalpel Of The Emperor","Price":3.2},{"SN":"Seuthelis34","Age":30,"Gender":"Female","Item ID":79,"Item Name":"Alpha, Oath of Zeal","Price":2.88},{"SN":"Styaduen40","Age":21,"Gender":"Female","Item ID":8,"Item Name":"Purgatory, Gem of Regret","Price":3.91},{"SN":"Ennoncil86","Age":32,"Gender":"Male","Item ID":120,"Item Name":"Agatha","Price":1.91},{"SN":"Lassassasda30","Age":15,"Gender":"Male","Item ID":120,"Item Name":"Agatha","Price":1.91},{"SN":"Tyeosri53","Age":31,"Gender":"Male","Item ID":10,"Item Name":"Sleepwalker","Price":1.73},{"SN":"Ilaststa70","Age":10,"Gender":"Female","Item ID":63,"Item Name":"Stormfury Mace","Price":1.27},{"SN":"Tyarithn67","Age":28,"Gender":"Male","Item ID":32,"Item Name":"Orenmir","Price":4.95},{"SN":"Streural92","Age":13,"Gender":"Male","Item ID":14,"Item Name":"Possessed Core","Price":1.59},{"SN":"Haellysu29","Age":21,"Gender":"Male","Item ID":91,"Item Name":"Celeste","Price":3.71},{"SN":"Yadaisuir65","Age":22,"Gender":"Male","Item ID":73,"Item Name":"Ritual Mace","Price":3.74},{"SN":"Aerithnucal56","Age":15,"Gender":"Male","Item ID":172,"Item Name":"Blade of the Grave","Price":1.69},{"SN":"Sundjask71","Age":15,"Gender":"Male","Item ID":77,"Item Name":"Piety, Guardian of Riddles","Price":3.68},{"SN":"Tyisriphos58","Age":38,"Gender":"Male","Item ID":101,"Item Name":"Final Critic","Price":4.62},{"SN":"Sundaststa26","Age":22,"Gender":"Female","Item ID":33,"Item Name":"Curved Axe","Price":1.35},{"SN":"Yalo71","Age":23,"Gender":"Male","Item ID":24,"Item Name":"Warped Fetish","Price":2.41},{"SN":"Mindetosya30","Age":16,"Gender":"Male","Item ID":67,"Item Name":"Celeste, Incarnation of the Corrupted","Price":2.31},{"SN":"Chanjaskan89","Age":23,"Gender":"Male","Item ID":15,"Item Name":"Soul Infused Crystal","Price":1.03},{"SN":"Chadjask77","Age":36,"Gender":"Male","Item ID":124,"Item Name":"Venom Claymore","Price":2.72},{"SN":"Lirtast83","Age":32,"Gender":"Male","Item ID":66,"Item Name":"Victor Iron Spikes","Price":3.55},{"SN":"Ingatcil75","Age":7,"Gender":"Male","Item ID":177,"Item Name":"Winterthorn, Defender of Shifting Worlds","Price":4.89},{"SN":"Lassassast73","Age":24,"Gender":"Male","Item ID":61,"Item Name":"Ragnarok","Price":3.97},{"SN":"Strairisti57","Age":18,"Gender":"Male","Item ID":157,"Item Name":"Spada, Etcher of Hatred","Price":2.21},{"SN":"Qarwen67","Age":11,"Gender":"Male","Item ID":176,"Item Name":"Relentless Iron Skewer","Price":2.97},{"SN":"Filrion59","Age":35,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Sondim43","Age":20,"Gender":"Male","Item ID":118,"Item Name":"Ghost Reaver, Longsword of Magic","Price":2.77},{"SN":"Aellysup38","Age":25,"Gender":"Male","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61},{"SN":"Hala31","Age":38,"Gender":"Male","Item ID":75,"Item Name":"Brutality Ivory Warmace","Price":1.72},{"SN":"Rithe77","Age":26,"Gender":"Female","Item ID":65,"Item Name":"Conqueror Adamantite Mace","Price":1.96},{"SN":"Marirrasta50","Age":19,"Gender":"Male","Item ID":159,"Item Name":"Oathbreaker, Spellblade of Trials","Price":3.01},{"SN":"Chanosiast43","Age":13,"Gender":"Female","Item ID":18,"Item Name":"Torchlight, Bond of Storms","Price":1.77},{"SN":"Sundim98","Age":20,"Gender":"Female","Item ID":100,"Item Name":"Blindscythe","Price":3.66},{"SN":"Frichaya88","Age":30,"Gender":"Male","Item ID":83,"Item Name":"Lifebender","Price":3.51},{"SN":"Lirtassa47","Age":27,"Gender":"Male","Item ID":25,"Item Name":"Hero Cane","Price":1.03},{"SN":"Iathenudil29","Age":29,"Gender":"Female","Item ID":130,"Item Name":"Alpha","Price":1.56},{"SN":"Lisirra55","Age":7,"Gender":"Female","Item ID":11,"Item Name":"Brimstone","Price":2.52},{"SN":"Yarolwen77","Age":24,"Gender":"Male","Item ID":46,"Item Name":"Hopeless Ebon Dualblade","Price":4.75},{"SN":"Crausirra42","Age":15,"Gender":"Female","Item ID":112,"Item Name":"Worldbreaker","Price":3.29},{"SN":"Frichast72","Age":23,"Gender":"Male","Item ID":87,"Item Name":"Deluge, Edge of the West","Price":2.2},{"SN":"Eulidru49","Age":16,"Gender":"Female","Item ID":33,"Item Name":"Curved Axe","Price":1.35},{"SN":"Aidain51","Age":26,"Gender":"Male","Item ID":81,"Item Name":"Dreamkiss","Price":4.06},{"SN":"Sida61","Age":24,"Gender":"Male","Item ID":40,"Item Name":"Second Chance","Price":2.34},{"SN":"Chamjasknya65","Age":20,"Gender":"Male","Item ID":23,"Item Name":"Crucifer","Price":2.77},{"SN":"Iri67","Age":15,"Gender":"Male","Item ID":128,"Item Name":"Blazeguard, Reach of Eternity","Price":4.0},{"SN":"Ririp86","Age":20,"Gender":"Female","Item ID":91,"Item Name":"Celeste","Price":3.71},{"SN":"Chadossa56","Age":37,"Gender":"Female","Item ID":117,"Item Name":"Heartstriker, Legacy of the Light","Price":4.15},{"SN":"Chanjaskan89","Age":23,"Gender":"Male","Item ID":26,"Item Name":"Unholy Wand","Price":1.88},{"SN":"Jiskimsda56","Age":21,"Gender":"Male","Item ID":93,"Item Name":"Apocalyptic Battlescythe","Price":3.91},{"SN":"Assistast50","Age":19,"Gender":"Male","Item ID":66,"Item Name":"Victor Iron Spikes","Price":3.55},{"SN":"Euliria52","Age":16,"Gender":"Male","Item ID":162,"Item Name":"Abyssal Shard","Price":2.04},{"SN":"Aerithriaphos45","Age":16,"Gender":"Male","Item ID":43,"Item Name":"Foul Edge","Price":2.38},{"SN":"Ila44","Age":15,"Gender":"Male","Item ID":170,"Item Name":"Shadowsteel","Price":1.98},{"SN":"Sida61","Age":24,"Gender":"Male","Item ID":128,"Item Name":"Blazeguard, Reach of Eternity","Price":4.0},{"SN":"Phyali88","Age":38,"Gender":"Male","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Iskossa88","Age":30,"Gender":"Male","Item ID":72,"Item Name":"Winter's Bite","Price":1.39},{"SN":"Aeral85","Age":25,"Gender":"Male","Item ID":115,"Item Name":"Spectral Diamond Doomblade","Price":4.25},{"SN":"Rinallorap73","Age":24,"Gender":"Male","Item ID":61,"Item Name":"Ragnarok","Price":3.97},{"SN":"Chanjask65","Age":36,"Gender":"Male","Item ID":5,"Item Name":"Putrid Fan","Price":1.32},{"SN":"Saedue76","Age":25,"Gender":"Male","Item ID":73,"Item Name":"Ritual Mace","Price":3.74},{"SN":"Assassa38","Age":34,"Gender":"Other \/ Non-Disclosed","Item ID":179,"Item Name":"Wolf, Promise of the Moonwalker","Price":1.88},{"SN":"Tyaelorgue39","Age":27,"Gender":"Female","Item ID":67,"Item Name":"Celeste, Incarnation of the Corrupted","Price":2.31},{"SN":"Tyananurgue44","Age":22,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Isketo41","Age":13,"Gender":"Male","Item ID":5,"Item Name":"Putrid Fan","Price":1.32},{"SN":"Sundast87","Age":21,"Gender":"Male","Item ID":159,"Item Name":"Oathbreaker, Spellblade of Trials","Price":3.01},{"SN":"Yadacal26","Age":24,"Gender":"Male","Item ID":37,"Item Name":"Shadow Strike, Glory of Ending Hope","Price":1.93},{"SN":"Ila44","Age":15,"Gender":"Male","Item ID":174,"Item Name":"Primitive Blade","Price":2.46},{"SN":"Ilophos58","Age":9,"Gender":"Male","Item ID":103,"Item Name":"Singed Scalpel","Price":4.87},{"SN":"Marilsanya48","Age":21,"Gender":"Male","Item ID":102,"Item Name":"Avenger","Price":4.16},{"SN":"Phially37","Age":22,"Gender":"Female","Item ID":79,"Item Name":"Alpha, Oath of Zeal","Price":2.88},{"SN":"Iduedru67","Age":25,"Gender":"Male","Item ID":169,"Item Name":"Interrogator, Blood Blade of the Queen","Price":3.32},{"SN":"Yarithsurgue62","Age":7,"Gender":"Male","Item ID":82,"Item Name":"Nirvana","Price":1.11},{"SN":"Aeduera68","Age":26,"Gender":"Male","Item ID":39,"Item Name":"Betrayal, Whisper of Grieving Widows","Price":2.35},{"SN":"Saidairiaphos61","Age":29,"Gender":"Male","Item ID":18,"Item Name":"Torchlight, Bond of Storms","Price":1.77},{"SN":"Tillyrin30","Age":20,"Gender":"Male","Item ID":69,"Item Name":"Frenzy, Defender of the Harvest","Price":1.06},{"SN":"Chanosiast43","Age":13,"Gender":"Female","Item ID":117,"Item Name":"Heartstriker, Legacy of the Light","Price":4.15},{"SN":"Quarusrion32","Age":15,"Gender":"Male","Item ID":14,"Item Name":"Possessed Core","Price":1.59},{"SN":"Chamimla73","Age":18,"Gender":"Male","Item ID":21,"Item Name":"Souleater","Price":3.27},{"SN":"Eurith26","Age":25,"Gender":"Male","Item ID":139,"Item Name":"Mercy, Katana of Dismay","Price":4.37},{"SN":"Tyananurgue44","Age":22,"Gender":"Male","Item ID":48,"Item Name":"Rage, Legacy of the Lone Victor","Price":4.32},{"SN":"Iskichinya81","Age":16,"Gender":"Male","Item ID":134,"Item Name":"Undead Crusader","Price":4.67},{"SN":"Hiadanurin36","Age":10,"Gender":"Female","Item ID":148,"Item Name":"Warmonger, Gift of Suffering's End","Price":3.96},{"SN":"Tyaelly53","Age":20,"Gender":"Female","Item ID":106,"Item Name":"Crying Steel Sickle","Price":2.29},{"SN":"Shidai42","Age":23,"Gender":"Female","Item ID":37,"Item Name":"Shadow Strike, Glory of Ending Hope","Price":1.93},{"SN":"Bartassaya73","Age":16,"Gender":"Male","Item ID":8,"Item Name":"Purgatory, Gem of Regret","Price":3.91},{"SN":"Mindosiasya28","Age":13,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Ethrusuard41","Age":10,"Gender":"Male","Item ID":16,"Item Name":"Restored Bauble","Price":3.11},{"SN":"Indirrian56","Age":19,"Gender":"Male","Item ID":45,"Item Name":"Glinting Glass Edge","Price":2.46},{"SN":"Sondim68","Age":22,"Gender":"Male","Item ID":101,"Item Name":"Final Critic","Price":4.62},{"SN":"Tyadaru49","Age":25,"Gender":"Male","Item ID":56,"Item Name":"Foul Titanium Battle Axe","Price":4.33},{"SN":"Cosadar58","Age":35,"Gender":"Female","Item ID":93,"Item Name":"Apocalyptic Battlescythe","Price":3.91},{"SN":"Farusrian86","Age":19,"Gender":"Male","Item ID":154,"Item Name":"Feral Katana","Price":2.19},{"SN":"Leyirra83","Age":24,"Gender":"Male","Item ID":145,"Item Name":"Fiery Glass Crusader","Price":4.45},{"SN":"Inguron55","Age":26,"Gender":"Male","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Haedasu65","Age":20,"Gender":"Male","Item ID":134,"Item Name":"Undead Crusader","Price":4.67},{"SN":"Ialistidru50","Age":21,"Gender":"Male","Item ID":130,"Item Name":"Alpha","Price":1.56},{"SN":"Sweecossa42","Age":20,"Gender":"Male","Item ID":79,"Item Name":"Alpha, Oath of Zeal","Price":2.88},{"SN":"Ralasti48","Age":35,"Gender":"Male","Item ID":34,"Item Name":"Retribution Axe","Price":4.14},{"SN":"Lamon28","Age":32,"Gender":"Male","Item ID":52,"Item Name":"Hatred","Price":4.39},{"SN":"Isri49","Age":15,"Gender":"Male","Item ID":120,"Item Name":"Agatha","Price":1.91},{"SN":"Frichassala85","Age":21,"Gender":"Male","Item ID":114,"Item Name":"Yearning Mageblade","Price":1.79},{"SN":"Eollym91","Age":23,"Gender":"Male","Item ID":86,"Item Name":"Stormfury Lantern","Price":1.28},{"SN":"Lisjasksda68","Age":26,"Gender":"Female","Item ID":179,"Item Name":"Wolf, Promise of the Moonwalker","Price":1.88},{"SN":"Yalostiphos68","Age":15,"Gender":"Female","Item ID":116,"Item Name":"Renewed Skeletal Katana","Price":2.37},{"SN":"Thryallym62","Age":20,"Gender":"Male","Item ID":4,"Item Name":"Bloodlord's Fetish","Price":2.28},{"SN":"Sondastan54","Age":31,"Gender":"Male","Item ID":104,"Item Name":"Gladiator's Glaive","Price":1.36},{"SN":"Ailaesuir66","Age":22,"Gender":"Female","Item ID":179,"Item Name":"Wolf, Promise of the Moonwalker","Price":1.88},{"SN":"Siasri67","Age":22,"Gender":"Male","Item ID":6,"Item Name":"Rusty Skull","Price":1.2},{"SN":"Seosri62","Age":35,"Gender":"Male","Item ID":11,"Item Name":"Brimstone","Price":2.52},{"SN":"Ryastycal90","Age":20,"Gender":"Male","Item ID":122,"Item Name":"Unending Tyranny","Price":1.21},{"SN":"Chanirrasta87","Age":19,"Gender":"Male","Item ID":87,"Item Name":"Deluge, Edge of the West","Price":2.2},{"SN":"Aerithllora36","Age":29,"Gender":"Male","Item ID":81,"Item Name":"Dreamkiss","Price":4.06},{"SN":"Raeduerin33","Age":28,"Gender":"Male","Item ID":175,"Item Name":"Woeful Adamantite Claymore","Price":1.24},{"SN":"Lisosiast26","Age":36,"Gender":"Male","Item ID":52,"Item Name":"Hatred","Price":4.39},{"SN":"Eurisuru25","Age":27,"Gender":"Other \/ Non-Disclosed","Item ID":48,"Item Name":"Rage, Legacy of the Lone Victor","Price":4.32},{"SN":"Assassasda84","Age":25,"Gender":"Male","Item ID":70,"Item Name":"Hope's End","Price":3.89},{"SN":"Aerithnucal56","Age":15,"Gender":"Male","Item ID":13,"Item Name":"Serenity","Price":1.49},{"SN":"Nitherian58","Age":22,"Gender":"Female","Item ID":84,"Item Name":"Arcane Gem","Price":2.23},{"SN":"Hailaphos89","Age":20,"Gender":"Male","Item ID":122,"Item Name":"Unending Tyranny","Price":1.21},{"SN":"Chamucosda93","Age":21,"Gender":"Male","Item ID":158,"Item Name":"Darkheart, Butcher of the Champion","Price":3.56},{"SN":"Frichilsasya78","Age":24,"Gender":"Male","Item ID":73,"Item Name":"Ritual Mace","Price":3.74},{"SN":"Aenasu69","Age":22,"Gender":"Male","Item ID":141,"Item Name":"Persuasion","Price":3.27},{"SN":"Lassista97","Age":24,"Gender":"Male","Item ID":25,"Item Name":"Hero Cane","Price":1.03},{"SN":"Sidap51","Age":15,"Gender":"Male","Item ID":31,"Item Name":"Trickster","Price":2.07},{"SN":"Chamadarsda63","Age":21,"Gender":"Male","Item ID":44,"Item Name":"Bonecarvin Battle Axe","Price":2.46},{"SN":"Lassassast73","Age":24,"Gender":"Male","Item ID":123,"Item Name":"Twilight's Carver","Price":1.14},{"SN":"Eural50","Age":22,"Gender":"Male","Item ID":98,"Item Name":"Deadline, Voice Of Subtlety","Price":3.62},{"SN":"Lirtossa78","Age":14,"Gender":"Male","Item ID":104,"Item Name":"Gladiator's Glaive","Price":1.36},{"SN":"Tillyrin30","Age":20,"Gender":"Male","Item ID":117,"Item Name":"Heartstriker, Legacy of the Light","Price":4.15},{"SN":"Quelaton80","Age":20,"Gender":"Male","Item ID":75,"Item Name":"Brutality Ivory Warmace","Price":1.72},{"SN":"Alim85","Age":23,"Gender":"Female","Item ID":107,"Item Name":"Splitter, Foe Of Subtlety","Price":3.61}]

# create function to add $ to number
def convert_to_currency(number): 
    return '${:.2f}'.format(number) 

# create function to add % to number
def convert_to_perc(number): 
    return '%{:.2f}'.format(number)

player_df=pd.DataFrame(player_dicts)
player_df.head()

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>38</td>
      <td>Male</td>
      <td>165</td>
      <td>Bone Crushing Silver Skewer</td>
      <td>3.37</td>
      <td>Aelalis34</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>119</td>
      <td>Stormbringer, Dark Blade of Ending Misery</td>
      <td>2.32</td>
      <td>Eolo46</td>
    </tr>
    <tr>
      <th>2</th>
      <td>34</td>
      <td>Male</td>
      <td>174</td>
      <td>Primitive Blade</td>
      <td>2.46</td>
      <td>Assastnya25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21</td>
      <td>Male</td>
      <td>92</td>
      <td>Final Critic</td>
      <td>1.36</td>
      <td>Pheusrical25</td>
    </tr>
    <tr>
      <th>4</th>
      <td>23</td>
      <td>Male</td>
      <td>63</td>
      <td>Stormfury Mace</td>
      <td>1.27</td>
      <td>Aela59</td>
    </tr>
  </tbody>
</table>
</div>




```
### Player Count

# count of unique players
counts = player_df['SN'].nunique()
counts

# Convert the player counts Series into a DataFrame
player_counts_df = pd.DataFrame({
    "Player Count": [counts]
})
player_counts_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Player Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>573</td>
    </tr>
  </tbody>
</table>
</div>




```
### Purchasing Analysis (Total)

#Number of Unique Items
unique=player_df["Item Name"].nunique()
unique

# Average Purchase Price
average=player_df["Price"].mean()
average

#Total Number of Purchases
counts = player_df['Item Name'].count()
counts

#Total Revenue
total=player_df["Price"].sum()
total

# Creating a summary DataFrame using above values

summary_df=pd.DataFrame({
    "Number of Unique Items": [unique],
    "Average Price": [average],
    "Number of Purchases":[counts],
    "Total Revenue ($)":[total]
})
summary_df.round(2)



```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Price</th>
      <th>Number of Purchases</th>
      <th>Number of Unique Items</th>
      <th>Total Revenue ($)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2.93</td>
      <td>780</td>
      <td>179</td>
      <td>2286.33</td>
    </tr>
  </tbody>
</table>
</div>




```
### Gender Demographics

grouped=player_df.groupby("Gender")

count=grouped.count()
count_all=player_df["Gender"].count()

#get count for each gender
count_female=count.loc['Female','Age']
count_male=count.loc['Male','Age']
count_other=count.loc['Other \/ Non-Disclosed','Age']

# Get percentages
PercMale= ((count_male/count_all)*100)  #.map(convert_to_perc)
PercFemale= (count_female/count_all)*100
PercOther= (count_other/count_all)*100



# Creating a summary DataFrame using above values

summary_df=pd.DataFrame({
    "Total Count": [count_female,count_male,count_other],
    "Percentage of Players (%)":[PercFemale,PercMale,PercOther],
    'Gender': ['Female','Male','Other']
})

summary_df
# set an existing column as the index
summary_df=summary_df.set_index('Gender')
summary_df.round(2)



```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Percentage of Players (%)</th>
      <th>Total Count</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>17.44</td>
      <td>136</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>81.15</td>
      <td>633</td>
    </tr>
    <tr>
      <th>Other</th>
      <td>1.41</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```
### Purchasing Analysis (Gender)

#Purchase Count- use count from above

# Average Purchase Price
avg_female=grouped["Price"].mean().loc['Female']
avg_male=grouped["Price"].mean().loc['Male']
avg_other=grouped["Price"].mean().loc['Other \/ Non-Disclosed']

#Total Purchase Value
tot_female=grouped["Price"].sum().loc['Female']
tot_male=grouped["Price"].sum().loc['Male']
tot_other=grouped["Price"].sum().loc['Other \/ Non-Disclosed']

#Normalized Totals
norm_female= tot_female/grouped["Price"].count().loc['Female']
norm_male=tot_male/grouped["Price"].count().loc['Male']
norm_other=tot_other/grouped["Price"].count().loc['Other \/ Non-Disclosed']

# Creating a summary DataFrame using above values

summary_df=pd.DataFrame({
    "Purchase Count": [count_female,count_male,count_other],
    "Average Purchase Price ($)":[avg_female,avg_male,avg_other],
    "Total Purchase Value ($)":[tot_female,tot_male,tot_other],
    "Normalized Totals ($)":[norm_female,norm_male,norm_other],
    'Gender': ['Female','Male','Other']
})

summary_df
# set an existing column as the index
summary_df=summary_df.set_index('Gender')
summary_df.round(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Purchase Price ($)</th>
      <th>Normalized Totals ($)</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value ($)</th>
    </tr>
    <tr>
      <th>Gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Female</th>
      <td>2.82</td>
      <td>2.82</td>
      <td>136</td>
      <td>382.91</td>
    </tr>
    <tr>
      <th>Male</th>
      <td>2.95</td>
      <td>2.95</td>
      <td>633</td>
      <td>1867.68</td>
    </tr>
    <tr>
      <th>Other</th>
      <td>3.25</td>
      <td>3.25</td>
      <td>11</td>
      <td>35.74</td>
    </tr>
  </tbody>
</table>
</div>




```
### Age Demographics

grouped=player_df.groupby("Age")

#Age Demographic

# Create Dataframe to hold count of players and sum of prices
count=grouped["Age"].count()
df=pd.DataFrame({
    "Count of Purchases":grouped["Age"].count(),
    "Count of Player":grouped["SN"].nunique(),
    "Sum of Price/Age":grouped["Price"].sum()
})
df

# Create bins in which to place values based upon age
bins = [0,10,14,19,24,29,34,39,120]

# Create labels for these bins
labels = [">10","10-14","15-19",'20-24',"25-29","30-34","35-39","40+"]

# reset index so that we can use Age column to cut
df.reset_index(level=0, inplace=True)

df["Group"]=pd.cut(df["Age"],bins,labels=labels)


# Creating a group based off of the bins
df = df.groupby("Group")



summary2_df=pd.DataFrame({
    "Total count of Players":df["Count of Player"].sum(),
    "Percentage of Players":(((df["Count of Player"].sum())/count_all)*100).map(convert_to_perc),
    "Purchase Count": df["Count of Purchases"].sum(),
    "Average Purchase Price": df["Sum of Price/Age"].mean().map(convert_to_currency),
    "Total Purchase Value":df["Sum of Price/Age"].sum().map(convert_to_currency),
    "Normalized Totals":(df["Sum of Price/Age"].sum()/df["Sum of Price/Age"].count()).map(convert_to_currency)
})
summary2_df.round(2)



```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Purchase Price</th>
      <th>Normalized Totals</th>
      <th>Percentage of Players</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
      <th>Total count of Players</th>
    </tr>
    <tr>
      <th>Group</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>&gt;10</th>
      <td>$24.16</td>
      <td>$24.16</td>
      <td>%2.82</td>
      <td>32</td>
      <td>$96.62</td>
      <td>22</td>
    </tr>
    <tr>
      <th>10-14</th>
      <td>$20.95</td>
      <td>$20.95</td>
      <td>%2.56</td>
      <td>31</td>
      <td>$83.79</td>
      <td>20</td>
    </tr>
    <tr>
      <th>15-19</th>
      <td>$77.28</td>
      <td>$77.28</td>
      <td>%12.82</td>
      <td>133</td>
      <td>$386.42</td>
      <td>100</td>
    </tr>
    <tr>
      <th>20-24</th>
      <td>$195.75</td>
      <td>$195.75</td>
      <td>%33.21</td>
      <td>336</td>
      <td>$978.77</td>
      <td>259</td>
    </tr>
    <tr>
      <th>25-29</th>
      <td>$74.07</td>
      <td>$74.07</td>
      <td>%11.15</td>
      <td>125</td>
      <td>$370.33</td>
      <td>87</td>
    </tr>
    <tr>
      <th>30-34</th>
      <td>$39.45</td>
      <td>$39.45</td>
      <td>%6.03</td>
      <td>64</td>
      <td>$197.25</td>
      <td>47</td>
    </tr>
    <tr>
      <th>35-39</th>
      <td>$23.88</td>
      <td>$23.88</td>
      <td>%3.46</td>
      <td>42</td>
      <td>$119.40</td>
      <td>27</td>
    </tr>
    <tr>
      <th>40+</th>
      <td>$13.44</td>
      <td>$13.44</td>
      <td>%1.41</td>
      <td>17</td>
      <td>$53.75</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>




```
grouped= player_df.groupby("SN")


players_df=pd.DataFrame({
    "Purchase Count":grouped["Price"].count(),
    "Average Purchase Price":grouped["Price"].mean().map(convert_to_currency),
    "Total Purchase Value": grouped["Price"].sum().map(convert_to_currency)
    })
players_df

#players.nlargest(5,'Total Purchase Value')

# sort Dataframe by Total purchase value
players_df=players_df.sort_values(by=['Total Purchase Value'],ascending=False)

#only show top 5 records
players_df.iloc[0:5]. round(2)

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Purchase Price</th>
      <th>Purchase Count</th>
      <th>Total Purchase Value</th>
    </tr>
    <tr>
      <th>SN</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Qarwen67</th>
      <td>$2.49</td>
      <td>4</td>
      <td>$9.97</td>
    </tr>
    <tr>
      <th>Sondim43</th>
      <td>$3.13</td>
      <td>3</td>
      <td>$9.38</td>
    </tr>
    <tr>
      <th>Tillyrin30</th>
      <td>$3.06</td>
      <td>3</td>
      <td>$9.19</td>
    </tr>
    <tr>
      <th>Lisistaya47</th>
      <td>$3.06</td>
      <td>3</td>
      <td>$9.19</td>
    </tr>
    <tr>
      <th>Tyisriphos58</th>
      <td>$4.59</td>
      <td>2</td>
      <td>$9.18</td>
    </tr>
  </tbody>
</table>
</div>




```
grouped= player_df.groupby(["Item ID","Item Name","Price"])
grouped["Item ID"].count()

item_df=pd.DataFrame({
    "Purchase Count": grouped["Item ID"].count(),
    "Total Purchase Value ($)":grouped["Price"].sum()
 
    })
item_df

# sort Dataframe by Total purchase value
item_df=item_df.sort_values(by=['Purchase Count'],ascending=False)

#only show top 5 records
item_df.iloc[0:5]. round(2)

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>Purchase Count</th>
      <th>Total Purchase Value ($)</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>39</th>
      <th>Betrayal, Whisper of Grieving Widows</th>
      <th>2.35</th>
      <td>11</td>
      <td>25.85</td>
    </tr>
    <tr>
      <th>84</th>
      <th>Arcane Gem</th>
      <th>2.23</th>
      <td>11</td>
      <td>24.53</td>
    </tr>
    <tr>
      <th>31</th>
      <th>Trickster</th>
      <th>2.07</th>
      <td>9</td>
      <td>18.63</td>
    </tr>
    <tr>
      <th>175</th>
      <th>Woeful Adamantite Claymore</th>
      <th>1.24</th>
      <td>9</td>
      <td>11.16</td>
    </tr>
    <tr>
      <th>13</th>
      <th>Serenity</th>
      <th>1.49</th>
      <td>9</td>
      <td>13.41</td>
    </tr>
  </tbody>
</table>
</div>




```
grouped= player_df.groupby(["Item ID","Item Name","Price"])
grouped["Item ID"].count()

item_df=pd.DataFrame({
    "Purchase Count": grouped["Item ID"].count(),
    "Total Purchase Value ($)": grouped["Price"].sum()
 
    })
#item_df['Total Purchase Value'] = item_df['Total Purchase Value']

# sort Dataframe by Total purchase value
item_df=item_df.sort_values(by=['Total Purchase Value ($)'],ascending=False)

#only show top 5 records
item_df.iloc[0:5]. round(2)
#item_df['Total Purchase Value'].max()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th>Purchase Count</th>
      <th>Total Purchase Value ($)</th>
    </tr>
    <tr>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>34</th>
      <th>Retribution Axe</th>
      <th>4.14</th>
      <td>9</td>
      <td>37.26</td>
    </tr>
    <tr>
      <th>115</th>
      <th>Spectral Diamond Doomblade</th>
      <th>4.25</th>
      <td>7</td>
      <td>29.75</td>
    </tr>
    <tr>
      <th>32</th>
      <th>Orenmir</th>
      <th>4.95</th>
      <td>6</td>
      <td>29.70</td>
    </tr>
    <tr>
      <th>103</th>
      <th>Singed Scalpel</th>
      <th>4.87</th>
      <td>6</td>
      <td>29.22</td>
    </tr>
    <tr>
      <th>107</th>
      <th>Splitter, Foe Of Subtlety</th>
      <th>3.61</th>
      <td>8</td>
      <td>28.88</td>
    </tr>
  </tbody>
</table>
</div>


