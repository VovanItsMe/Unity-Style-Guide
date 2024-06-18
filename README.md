# Unity Style Guide

Эта статья содержит то, какая структура, нейминг для скриптов и ассетов должны использоваться в структуре проекта Unity. 

<a name="toc"></a>
## Содержание

> 1. [Вступление](#introduction)
> 1. [Структура Проекта](#structure)
> 1. [Скрипты](#scripts)
> 1. [Правила Нейминга Ассетов И Назначение Лейблов](#anc)
> 1. [Asset Workflows](#asset-workflows)

<a name="introduction"></a>
## 1. Вступление

### Разделы

> 1.1 [Стиль](#style)

> 1.2 [Базовая Терминология](#importantterminology)

<a name="style"></a>
### 1.1 Стиль

#### Если у вашей команды существует стайл гайд, вы должны ему следовать.
Если Вы работаете над проектом, в команде, которая следует стайл гайду, Вы также должны ему следовать. Все несоответствия между вашим стилем и прописанным в гайде не должны существовать.

Стайл гайд не является константой - он может быть изменён, при наличии непрописанных ситуаций, если это действительно необходимо.

> ##### *Споры о стиле бессмысленны. Существует стайл гайд, и ты обязан ему следовать.*
> [_Rebecca Murphey_](https://rmurphey.com)

#### Вся структура, ассеты и код, должны выглядеть так, будто их создал один человек. Не важно сколько людей работали над ними.
При переходе с одного проекта на другой, не должно быть различий в стиле и структуре.

Соблюдение единого стиля устраняет хаос в структуре проекта.

Общий стиль позволяет без проблем поддерживать проект, не нужно думать о его новой структуре, просто следуй инструкциям. Этот стайл гайд написан с учётом всех известных проблем, так что, если они возникнут, их будет проще отследить.

#### Друзья, не позволяйте вашим друзьям вносить беспорядок в проект.
Если Вы видите, что кто-то не следует стилю - поправьте их.

При работе в команде, заметно легче помочь и попросить о помощи, когда люди объединены. Никому не нравится искать проблему там, где он видит только беспорядок.

Если вы помогаете человеку, который следует, пусть и другому, но стилю - вам проще приспособиться к нему. Если же стиля нет - посоветуйте ему сначала поработать над ним.


<a name="importantterminology"></a>
### 1.2 Базовая Терминология

<a name="terms-prefab"></a>
#### Префабы
Unity использует термин “Префаб” (“Prefab”) для системы, которая позволяет создавать, настраивать, и хранить “Игровой Объект” (“GameObject”), вместе со всеми компонентами, конкретными значениями, и дочерними “Игровыми Объектами”, как многоразового ассета, представляя, своего рода, контейнер.

<a name="terms-label"></a>
#### Лейблы
Лейблы (“Label”) используются для упрощения поиска, однако давать лейбл нужно только префабам, потому как у них нет префикса.

<a name="terms-level-map"></a>
#### Уровни/Карты/Сцены
В Unity существуют сцены, однако часто люди называют их уровнями или же картами. Простыми словами - сцены содержат в себе множества объектов.

<a name="terms-serializable"></a>
#### Serializable
Переменные, которые Serializable показываются в окне “Инспектора” (“Inspector”) в Unity. Больше информации вы найдёте в документации к Unity, в статье [Serializable](https://docs.unity3d.com/Manual/script-Serialization.html).

<a name="terms-cases"></a>
#### Cases
Существует несколько вариантов того, как вы можете называть вещи. Вот несколько примеров:

> ##### PascalCase
> Каждое слово пишется с заглавной буквы, без пробелов: `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.
> 
> ##### camelCase
> Каждое слово пишется с заглавной буквой, но первое слово начинается с прописной: `desertEagle`, `styleGuide`, `aSeriesOfWords`.
>  ##### lowercase
> Все буквы прописные - `deserteagle`, 
>
> ##### Snake_case
> Слова могут начинаться как с заглавной, так и с прописной, однако слова разделяет нижнее подчёркивание: `desert_Eagle`, `Style_Guide`, `a_Series_of_Words`.

**[⬆ Вверх](#table-of-contents)**

<a name="structure"></a>
## 2. Структура проекта
Стиль структуры проекта должен считаться законом. Нейминг ассетов и папок должны соответствовать друг другу, несоответствие хотя бы одного элемента может привести к беспорядку “на ровном месте”.

Данный стиль и структура оптимизированы как для простого перемещения между папок, так и для поиска в окне “Проекта” (“Project”), подобный формат имеет преимущества над стилями, использующими иную структуру и нейминг.

> Использование префикса [правил нейминга](#asset-name-modifiers), хранение в папках однотипных ассетов как: `Меши`, `Текстуры`, и `Материалы` – является излишним поскольку типы ассетов уже отсортированы по префиксу и могут быть отфильтрованы в поиске.
<pre>
	Структура проекта должна выглядеть подобным образом:
Assets
    _Developers (Использование `_` помещает файл вверх)
        DeveloperName (Личная папка разработчика, в ней содержатся тестовые ассеты, которые не попадут в финальный проект и будут удалены при мёрдже)
    ProjectName (Основная папка проекта)
		GameModes (Содержит файлы для игровых режимов)
            	Objects (Содержит модели с текстурами и материалами, бесшовные текстуры с материалами, анимационные контроллеры и анимационные клипы, карты высот для построения террейнов, оптимизированные и финализированные составные элементы отдельных карт)
                	Environment 
(Содержит модели с текстурами и материалами)

				Architecture (Содержит большие постройки)
					Buildings (Содержит здания)
						Hangar
							Materials
							Textures
				Common (Содержит модели окружения)
					Big 
			(Большие, по типу: бочек, заборов, фонарей и тп.)

					Small 
			(Маленькие, по типу: коробок, мусорных пакетов и тп.)

				Ground (Содержит файлы разметки, трещин и тп.)
				Industrial (Содержит большие модели окружения, относящиеся к индустриализации, по типу: портовые и строительные краны, большие цистерны с топливом, электроопоры, вышки, морские контейнеры и тп.)

				Military (Содержит модели, относящиеся к оборонительным сооружениям, военной технике и тп.)

				Nature (Содержит объекты природного происхождения, по типу: травы, деревьев, кустов, камней и тп.)

				Transport (Содержит транспорт)
					Aircraft (Воздушный)
					Cars (Наземный)
					Ships (Водный)
			Gameplay 
(Содержит объекты для геймплея)

				Drones 
(Содержит модели дронов с их текстурами и материалами)

				Maps (Содержит оптимизированные и финализированные составные элементы отдельных карт)
					City
			General
				Animations (Содержит анимационные клипы с анимационными контроллерами, как общие, так и для конкретных объектов)

				MapHeightmaps 
(Содержит карты высот для построения террейнов)

				SeamlessMaterials 
(Содержит бесшовные материалы с их текстурами)

		Prefabs 
(Содержит файлы префабов, та же иерархия папок, как и в папках объектов)

			CompositionPrefabs (Содержит трафареты для построения шаблонных локаций и сборные композиции, часто применяемые на сценах)

				Architecture
				Common
				Ground
				Industrial
				Military
				Nature
				Transport
			Environment (Содержит отдельные и собранные префабы)
				Architecture
				Common
				Ground
				Industrial
					Container (Отдельные префабы)
						Complete (Собранные префабы)
				Military
				Nature
				Transport
			Gameplay 
(Содержит объекты префабов, необходимые для работы игры)

		Resources (Содержит загружаемые ресурсы, те что грузятся из кода)
		Scenes 
(Содержит сцены и файлы для их настройки, к примеру - профили постобработки)
			BootScene (Сцена запуска и файлы к ней)
			GameMaps (Игровые сцены и файлы к ним)
				City
			MTS ()
            Scripts

            Sound

            UI (Содержит файлы элементов интерфейса и файлы для его работы)
		Fonts (Файлы шрифтов)
		Image ()
		Materials ()
		Prefabs ()
		Scripts ()
    Plugins (Содержит сторонние пакеты, аддоны)
    ImportedAssets (Содержит сторонние файлы)
    Resources (Содержит загружаемые ресурсы, те что грузятся из кода)
</pre>

Причины использования данной структуры описаны ниже, в подразделах.

### Подразделы

> 2.1 [Названия Папок](#structure-folder-names)

> 2.2 [Корневая Папка](#structure-top-level)

> 2.3 [Личные Папки Разработчиков](#structure-developers)

> 2.4 [Сцены](#levels)

> 2.5 [Разделение Ответственности](#structure-ownership)

> 2.6 [`Assets` или `AssetTypes`](#structure-assettypes)

> 2.7 [Большие Композиции Должны Иметь Свои Папки](#structure-large-sets)

> 2.8 [Библиотека Материалов](#structure-material-library)

> 2.9 [Структура Сцены](#scene-structure)


<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Наименования папок
Базовые правила наименования папок в структуре проекта.

<a name="2.1.1"></a>
#### Обязательный стиль названия - [PascalCase](#terms-cases)
PascalCase значит, что слова начинаются с заглавной буквы и не имеют пробела между друг другом. Пример: `DesertEagle`, `RocketPistol` и `ASeriesOfWords`.

<a name="2.1.2"></a>
#### Никогда Не Используй Пробелы
Дополнение [2.1.1](#2.1.1), никогда не используй пробелы. Пробелы могут создавать проблемы для различных инструментов и процессов. В идеале путь к вашему проекту на компьютере должен выглядеть так `“D:\Project”`, вместо `“C:\Users\My Name\My Documents\Unity Projects”`.

<a name="2.1.3"></a>
#### Никогда Не Используй Специальные Символы И Знаки Unicode
примеру, в вашем проекте имеется персонаж с именем 'Zoë', значит его файл должен называться “Zoe”. Символы Unicode могут создать даже больше проблем чем [Пробелы](#2.1.2) потому как для некоторых инструментов и частей программ могут не поддерживаться символы Unicode в пути к файлам.

К слову, если имя пользователя на вашем пк содержит символы Unicode (т.е. имя пользователя `“Zoë”`), любой проект, находящийся в папке `“My Documents”` будет страдать от этой проблемы. Обычно перемещение в корневую папку диска, к примеру `“D:\Project”` может исправить связанные с этим проблемы.

Использование спец. символов по типу: `a-z`, `A-Z`, и `0-9` а также `@, -, _, ,, *`, и `#` таким же образом может повлечь за собой: труднодиагностируемые проблемы на других платформах, контроль версий, некорректную работу различных инструментов и тд.

<a name="structure-no-empty-folders"></a>
#### НЕТ Пустым Папкам
В проекте не должно быть пустых папок. Они мешают при поиске.
Если же вы нашли пустую папку, нельзя просто так взять и удалить её, сначала нужно убедиться в следующем:
1.	Убедитесь, что вы на актуальной версии ветки.
2.	Спросите у своих коллег, необходима ли им эта папка.
3.	Откройте папку через проводник для проверки скрытых файлов и удалите их.
4.	Перейдите в проект и убедитесь, что его работа не нарушена.
5.	Убедитесь, что папка удалена.
6.	Закоммитьте внесённые изменения.

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Используйте Корневую Папку Только Для Особых Ассетов
Все ассеты проекта должны находиться в папках, находящихся внутри папки с названием проекта. К примеру, ваш проект называется 'Generic Shooter', всё его содержимое находится по пути “Assets/GenericShooter”.
Папка “Developers” нужна, для вашей личной папки, в которой могут содержаться ваши файлы, для, например, тестирования. Смотрите [Папки Разработчиков](#2.3) для более детальной информации.

Существует множество причин, по которым необходима такая структура.

<a name="2.2.1"></a>
#### НЕТ Глобальным Ассетам
Довольно часто в код стайл гайдах написано, что не следует использовать без особых причин глобальные пространства имён, ровно по тем же причинам. В случае, когда ассеты находятся в корневой папке, они не следуют общему стилю, а это обязательно приводит к хаосу, потому как нет нужды распределять ассеты должным образом.

У каждого ассета должно быть своё предназначение, иначе он не должен находиться в проекте. Если ассет предназначен для тестирования и не будет, в дальнейшем, использован с проекте, он должен находиться в вашей личной папке, в папке [Developers](#2.3).


<a name="2.2.2"></a>
#### Уменьшить Конфликты При Переиспользовании
При работе над несколькими проектами, копирование различных ассетов из одного проекта в другой – обычное дело.

Во избежание проблем при переносе, хорошей практикой будет помещение всех импортных ассетов в папку уровнем выше (основная папка `“Assets”`).

<a name="2.2.2e1"></a>
##### Пример Основного Материала
Скажем, Вы создали материал, который хотите использовать в нескольких проектах сразу, вот, Вы скопировали его в другой проект. Можете не помещать его в корневую папку, если путь к нему выглядит так `“Assets/MaterialLibrary/M_Master”`. При условии, что в проекте, в который происходит перенос, не существует материала с таким названием. В этом случае проблемы не возникнут.

В процессе работы, скопированные материалы могут изменяться под нужды конкретного проекта.

Однако проблемы могут возникнуть, когда необходимо будет перенести КОМПОЗИЦИЮ, состоящую из разных ассетов, в другой проект, при этом она будет использовать основной материал, к примеру, расположенный по пути `“Assets/MaterialLibrary/M_Master”`, если, как в случае, описанном выше, у нас находится по этому же пути изменённый материал, тогда в ассетах композиции будет использован изменённый материал, это и приведёт к дальнейшим проблемам.

Подобную проблему трудно предсказать и бывает трудно заметить, потому что тот, кто перемещает КОМПОЗИЦИЮ может быть не тем, кто её составлял и не знать, что они используют основной материал по тому же пути. The Migrate tool требуется вся цепочка зависимых ассетов, в свою очередь это требует перемещения материала по пути `"Assets/MaterialLibrary/M_Master"` при копировании, может получиться так, что он заменит существующие файлы проекта теми, которые он переносит.

В случае, если скопированные материалы изменились, вы рискуете столкнуться с проблемами, в виде нарушения зависимостей ассетов, расположенных по тому же пути, что и в оригинальном проекте, из-за того, что перенесённые ассеты были распределены по всему проекту, вместо нахождения в отведённой для этого папки. Таким образом, казалось бы, банальное перемещение ПРЕФАБОВ моделей может стать очень проблемным занятием.

<a name="2.2.3"></a>
#### Тестовые Файлы, Шаблоны, и Сторонние Ассеты Безопасны
Дополнение к [2.2.2](#2.2.2), если член команды добавил тестовые файлы, файлы шаблонов или сторонние ассеты, в большинстве случаев они не нарушат работу проекта, но только в случае, если имя корневой папки не было изменено.

Однако необязательно, чтобы сторонние ассеты следовали [правилу корневой папки](#2.2). Существует множество пакетов, большинство файлов которых расположено в корневой папке, но также возможно без проблем перенести их в основную папку проекта для освобождения корневой.

При соблюдении [2.2](#2.2), худший конфликт сторонних ассетов - если несколько пакетов имеют одинаковые тестовые файлы. Если все ваши ассеты находятся в папке проекта, включая тестовые файлы, их следует переместить в вашу папку в _Developers, такой подход поможет избежать подобных конфликтов.

#### Дополнения, Подпроекты, и Патчи Легко Поддерживать
Если предполагается разработка дополнений (DLC) к вашему проекту, или же с ним связано множество подпроектов которые будут перенесены или просто не добавлено в билд, относящиеся к ним ассеты должны находиться в корневой папке.
Подобное отделение DLC значительно упрощает работу над проектом. Подпроекты также могут добавляться и удаляться без особых усилий.

Если вам нужно изменить материал ассета или добавить какой-либо ассет, заменяющий другой, в патче, вы можете просто добавить его в папку для патча и продолжить работу, зная, что основной проект не повредится.

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Используй Папку Разработчика Для Тестирования
При разработке проекта, очень часто членам команды нужна тестовая площадка, которая не повредит основной проект.
Поскольку работа ведётся непрерывно, эти разработчики могут захотеть запушить свои изменения. Не везде есть правило, что нужно использовать папку разработчика, однако без неё есть шанс получить конфликт при работе с гитом.

Как только работа над файлами будет завершена – разработчик просто переместит их в папку основного проекта.

После окончания работы над своей веткой и мёржде в develop, все данные из личной папки данного разработчика в папке _Developers должны быть удалены самим разработчиком, либо ревьюиром.

<a name="levels"></a>
### 2.4 Все Файлы для [Сцены](#terms-level-map) Должны Находиться в Папке “Уровни”
Файлы для уровней особенные и обычно для них в каждом проекте существует своя система нейминга, особенно, если идёт работа над подпроектами или `streaming levels`. Не имеет значения, какая система структуризации карт для каждого проекта, все уровни должны находиться по пути `"Assets/ProjectNameName/Levels"`.

Возможность сказать кому-то открыть конкретную карту, без объяснения где она находится может сэкономить много времени, а также повысить “качество жизни”. Обычно для каждого уровня существуют подпапки в папке `"Levels"`, например `"Levels/Campaign1/"` или `"Levels/Arenas"`, но самая важное то, что все они находятся в единой папке `"Assets/ProjectNameName/Levels"`.

Это также способствует облегчению билда для инженеров. Поиск сцен может затянуться, если искать их по всему проекту. Если же все сцены находятся в одной папке “потерять” их при билде становится трудно. Это так же упрощает сборку освещения и QA processes.

<a name="2.5"></a>
<a name="structure-ownership"></a>
### 2.5 Разделение Ответственности
В командах, где больше одного разработчика, стоит разделять ответственность по зонам/ассетам/функционалу. Некоторые ассеты вроде сцен и префабов не могут адекватно обработать изменения от нескольких людей, создавая конфликты.
В таких случаях стоит назначить одного человека (или дать право на изменения), что позволит избежать подобных конфликтов.

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Не Создавать Папки С Названием `Assets` или `AssetTypes`

<a name="2.6.1"></a>
#### Создание папки Assets излишне.
Все ассеты - ассеты.

<a name="2.6.2"></a>
#### Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant.
`All asset names are named with their asset type in mind. These folders offer only redundant information and the use of these folders can easily be replaced with the robust and easy to use filtering system the Content Browser provides.`

`Want to view only static mesh in `Environment/Rocks/`? Simply turn on the Static Mesh filter. If all assets are named correctly, they will also be sorted in alphabetical order regardless of prefixes. Want to view both static meshes and skeletal meshes? Simply turn on both filters. this eliminates the need to potentially have to `Control-Click` select two folders in the Content Browser's tree view.`

> `This also extends the full path name of an asset for very little benefit. The `SM_` prefix for a static mesh is only three characters, whereas `Meshes/` is seven characters.`

`Not doing this also prevents the inevitability of someone putting a static mesh or a texture in a `Materials` folder`.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Большие Композиции Должны Иметь Свои Папки

Это можно расценивать как псевдо-исключение из [2.6](#2.6).

Существует несколько типов ассетов, которые объединяют огромное количество файлов, при этом имея уникальное применение. Обычно это звуковые файлы и файлы анимации. Если в вашем проекте количество связанных файлов 15 и более, они должны быть вместе.

Например, анимационные клипы для нескольких персонажей должны находиться в `"Characters/Common/Animations"`, также могут быть подпапки Locomotion или Cinematic.

Это не применимо к таким файлам как текстуры и материалы. К примеру, папка Rocks содержит множество текстур при большом количестве моделей камней, однако разные текстуры принадлежат разным камням и должны иметь соответствующее название. Даже если эти текстуры находятся в [Библиотеке Материалов](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `Библиотека Материалов`

Если в вашем проекте используются общие материалы, layered materials, или иные формы переиспользуемых материалов и текстур которые не принадлежат конкретным ассетам, они должны находиться в `"Assets/ProjectName/MaterialLibrary"`.

Таким образом “глобальные” материалы будут иметь своё место, в котором их легко найти.
Это также позволяет легко следовать указанию 'use material instances only' в проекте. Если все должны использовать material instances, тогда только обычные материалы должны находиться в этой папке. Вы можете легко отследить это искав только base материалы, не расположенные в `MaterialLibrary`.

`MaterialLibrary` не обязана содержать исключительно материалы. Shared utility textures, material functions, и другие файлы подобного назначения должны находиться в папках, отражающих их назначение. Например, generic noise textures должны находиться в `"MaterialLibrary/Utility"`.

Все тестовые материалы или материалы для дебага должны находиться в `"MaterialLibrary/Debug"`. Это позволяет быстро вырезать материалы для дебага из проекта перед переносом и делает ошибки более очевидными, если ассеты проекта используют их.

<a name="2.9"></a>
<a name="scene-structure"></a>
## 2.9 Структура Сцены
Уходя от иерархии проекта, переходим к иерархии сцены. Как и раньше, это лишь шаблон. Вы можете подстроить его под свои нужды.

Используйте Пустые Объекты (Create Empty) как папки на сцене.

<pre>
Debug
Management
UI
Cameras
Lights
World
    Terrain
    Props
Gameplay
	Actors
	Items
_Dynamic
</pre>

-	У всех родительских объектов (пустых), должны быть координаты 0,0,0 со стандартными скейлом и вращением.
-	Для пустых объектов, которые являются объектами для скриптов, используйте “@” как префикс – “@Cheats”
-	Когда вы инициализируете объекты в runtime, убедитесь, что они находятся в _Dynamic – не забивайте основную иерархию, в противном случае вам будет трудно ориентироваться в ней.


**[⬆ Вверх](#table-of-contents)**

<a name="scripts"></a>

## 3. Скрипты

Этот раздел будет сфокусирован на классах C# и их содержимом. Если это возможно, соблюдайте стиль, соответствующий стандартам Microsoft C#.

### Sections
> 3.1 [Организация Классов](#classorganization)

> 3.2 [Компиляция](#compiling)

> 3.3 [Переменные](#variables)

> 3.4 [Функции](#functions)

<a name="classorganization"></a>
### 3.1 Организация Классов
Файлы скриптов должны содержать только публичные типы, однако допустимы подклассы.

Source файлы должны именоваться также как публичный класс.

Делайте организацию пространства имён с чёткой структурой,

Группы классов должны быть расположены в алфавитном порядке и сгруппированы по секторам:

* Constant Fields
* Static Fields
* Fields
* Constructors
* Properties
* Events / Delegates
* LifeCycle Methods (Awake, OnEnable, OnDisable, OnDestroy)
* Public Methods
* Private Methods
* Nested types
* Debug

Каждая из этих групп отсортирована по модификаторам доступа:
* public
* internal
* protected
* private
```
namespace ProjectName
{
	/// <summary>  
	/// Краткое описание того, что делает класс
	/// </summary>
    public class Account
    {
      #region Fields
      
      [Tooltip("Публичные переменные устанавливаемые в Инспекторе, должны иметь Подсказку")]
      public static string BankName;
      
	  /// <summary>  
	  /// Они также должны иметь описание
	  /// </summary>
      public static decimal Reserves;
 
	  public string BankName;
	  public const string ShippingType = "DropShip";
	  
	  private float _timeToDie;
	  
	  #endregion
	  
	  #region Properties
	  
      public string Number {get; set;}
      public DateTime DateOpened {get; set;}
      public DateTime DateClosed {get; set;}
      public decimal Balance {get; set;}
            
	  #endregion
	 
	  #region LifeCycle
	  
      public Awake()
      {
        // ...
      }
      
      #endregion
	  #region Public Methods
	  
      public AddObjectToBank()
      {
        // ...
      }
      
      #endregion
    }
}
```

#### Шаблоны Скриптов
Чтобы сэкономить немного времени можно переписать стандартный шаблон скриптов Unity своим собственным, для автоматической настройки пространств имён, регионов и тп. Изучите как это сделать в Unity [support](https://support.unity3d.com/hc/en-us/articles/210223733-How-to-customize-Unity-script-templates).

<a name="namespace"></a>
#### Namespace
Используйте namespace чтобы убедиться, что обзор classes/enum/interface/etc не будет вступать в конфликты с существующими namespaces или global namespace.
В проекте должно использоваться минимальное количество the projects name для Namespace чтобы избежать конфликтов со сторонними ассетами.

#### Все Публичные Функции Должны Иметь Описание

Всё просто – любая функция, имеющая модификатор доступа Public должна иметь описание.

```
/// <summary>
/// Стрельба из пистолета
/// </summary>
public void Fire()
{
// Выстрел из пистолета.
}
```

#### Foldout Groups
Если класс содержит небольшое количество переменных, Foldout Groups не обязательны.

При условии, что класс содержит много (5-10) переменных, все [Serializable](#serializable) переменные должны иметь нестандартные применённые Foldout Group. Обычно они относятся к категории `Config`.

Для того, чтобы создать Foldout Groups существует 2 способа в Unity. 

* Первый - это определить `[Serializable] public Class` внутри главного класса, однако это может повлиять на производительность. Это позволит многократно использовать одно имя для переменной.
* Второй вариант – это использовать Foldout Group Attribute доступный в [Odin Inspector](https://odininspector.com/).

```
[[Serializable](https://docs.unity3d.com/ScriptReference/Serializable.html)]
public struct PlayerStats
	{
        public int MovementSpeed;
    }
    
[FoldoutGroup("Interactable")]
public int MovementSpeed = 1;
```

#### Комментирование
Комментарии должны описывать intention, algorithmic overview, и/или logical flow.

В идеале, читая комментарии, любой должен понять, за что отвечает скрипт, а не только тот, кто его разрабатывал.

Нет установленной длины комментария, очевидные и короткие методы не обязательно должны иметь комментарии, однако подавляющее большинство методов должно их иметь, чтобы отражать подход и намерения программиста.

##### Стиль комментариев
Располагайте комментарии на отдельных строках, а не в конце строки после кода.

Пишите комментарии начиная с заглавной буквы.

В конце комментария ставится точка.

Ставьте пробел после (//) в тексте, как показано в примере.

Подобный стиль комментария - // (две косые черты), должен использоваться в большинстве ситуаций. Где возможно – оставляйте комментарии над кодом, а не возле него.

Пример:

```
        // Простой комментарий над переменной.
        private int _myInt = 5;
```

#### Регионы
Регионы `“#region”` позволяют сворачивать отмеченные ими части кода в скриптах C#. Возможность сворачивать части кода выборочно делает его удобнее и читаемее.

Пример:

```
#region "This is the code to be collapsed"
    Private components As System.ComponentModel.Container
#endregion
```

#### Промежутки
Ставьте пробел после запятой, при перечислении аргументов.

Example: `Console.In.Read(myChar, 0, 1);`
* Не ставьте пробел после скобок и аргументов функции.
* Не ставьте пробел между названием функции и скобкой.
* Не ставьте пробел в скобках (квадратных). 

<a name="3.1"></a>
<a name="compiling"></a>
### 3.2 Компиляция
Все скрипты должны быть скомпилированы без предупреждений и ошибок. При возникновении подобных, их необходимо скорее исправить, потому как могут возыметь непредвиденные и серьёзные последствия.

*Ни в коем случае* **нельзя** пушить скрипты с ошибками.

### 3.3 Переменные
Слова `переменная` и `свойство` для вас должны означать одно и то же и быть взаимозаменяемыми. 

#### Названия Переменных

##### Nouns
Все небулевые переменные должны быть понятным, однозначными и быть существительными.

##### Case
Все переменные должны использовать PascalCase, кроме [private](#privatevariables), использующие camelCase. 

Используй PascalCase для аббревиатур из 4-х или более букв (из 3-х символов 2 заглавные).

##### Considered Context
Все переменные должны иметь название, сопоставимое с их предназначением.

###### Примеры Considered Context:
Возьмём класс `PlayerCharacter`.

**Плохо**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

Все переменные имеют излишне длинное название. Подразумевается, что они относятся к классу `PlayerCharacter`, однако класс, в котором они находятся и есть `PlayerCharacter`.

**Хорошо**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

#### Уровень Доступа к Переменным
В C# у переменных есть модификатор доступа.

Public означает, что к данной переменной можно получить доступ вне скрипта (или класса).

Protected означает, что только дочерние классы и сам класс имеет доступ к переменной.

Private означает, что переменная доступна исключительно для этого класса.

Переменные должны быть публичными **только в случае необходимости**.

Лучше использовать `[SerializeField]`, вместо обозначения её Public.

##### Локальные Переменные
Локальные переменные должны именоваться по camelCase.

###### Неявное Типизирование Локальных Переменных
Используйте скрытые типы для локальных переменных если тип переменной явно виден из её значения по правую сторону равенства, или когда точный тип не важен.

```
var var1 = "Очевидно, это string.";
var var2 = 27;
var var3 = Convert.ToInt32(Console.ReadLine());
// Also used in for loops
for (var i = 0; i < bountyHunterFleets.Length; ++i) {};
```

Не используйте var, если тип не очевиден из значения переменной.
Пример:

```
int var4 = ExampleClass.ResultSoFar();
```

<a name="privatevariables"></a>
##### Private Variables
Private variables should have a prefix with a underscore `_myVariable` and use camelCase.

Unless it is known that a variable should only be accessed within the class it is defined and never a child class, do not mark variables as private. Until variables are able to be marked `protected`, reserve private for when you absolutely know you want to restrict child class usage.

##### Do _Not_ use Hungarian notation
Do _not_ use Hungarian notation or any other type identification in identifiers
```
// Correct
int counter;
string name;
 
// Avoid
int iCounter;
string strName;
```

#### Variables accessible in the Editor

##### Tooltips 
All [Serializable](#serializable) variables should have a description in their `[Tooltip]` fields that explains how changing this value affects the behavior of the script.

##### Variable Slider And Value Ranges
All [Serializable](#serializable) variables should make use of slider and value ranges if there is ever a value that a variable should _not_ be set to.

Example: A script that generates fence posts might have an editable variable named `PostsCount` and a value of -1 would not make any sense. Use the range fields `[Range(min, max)]` to mark 0 as a minimum.

If an editable variable is used in a Construction Script, it should have a reasonable Slider Range defined so that someone can not accidentally assign it a large value that could crash the editor.

A Value Range only needs to be defined if the bounds of a value are known. While a Slider Range prevents accidental large number inputs, an undefined Value Range allows a user to specify a value outside the Slider Range that may be considered 'dangerous' but still valid.

#### Variable Types

##### Booleans

###### Boolean Prefix
All booleans should be named in PascalCase but prefixed with a verb.

Example: Use `isDead` and `hasItem`, **not** `Dead` and `Item`.

###### Boolean Names
All booleans should be named as descriptive adjectives when possible if representing general information.

Try to not use verbs such as `isRunning`. Verbs tend to lead to complex states.

###### Boolean Complex States
Do not use booleans to represent complex and/or dependent states. This makes state adding and removing complex and no longer easily readable. Use an enumeration instead.

Example: When defining a weapon, do **not** use `isReloading` and `isEquipping` if a weapon can't be both reloading and equipping. Define an enumeration named `WeaponState` and use a variable with this type named `WeaponState` instead. This makes it far easier to add new states to weapons.

##### Enums
Enums use PascalCase and use singular names for enums and their values. Exception: bit field enums should be plural. Enums can be placed outside the class space to provide global access.

Example: 
```
public enum WeaponType
{
    Knife,
    Gun
}

// Enum can have multiple values
[Flags]
public enum Dockings
{
	None = 0,
	Top = 1,
}

public WeaponType Weapon
```

##### Arrays
Arrays follow the same naming rules as above, but should be named as a plural noun.

Example: Use `Targets`, `Hats`, and `EnemyPlayers`, not `TargetList`, `HatArray`, `EnemyPlayerArray`.

##### Interfaces
Interfaces are led with a capital `I` then followed with PascalCase.

Example: ```public interface ICanEat { }```

<a name="functions"></a>
### 3.4 Functions, Events, and Event Dispatchers
This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

#### Function Naming
The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Is it a pure function?
* Is it fetching state information?
* Is it a handler?
* What is its purpose?

These questions and more can all be answered when functions are named appropriately.

<a name="function-verbrule"></a>
#### All Functions Should Be Verbs
All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should start with verbs. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

Good examples:

* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `Jump` - Good example if in a Character class, otherwise, needs context.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:

* `Dead` - Is Dead? Will deaden?
* `Rock`
* `ProcessData` - Ambiguous, these words mean nothing.
* `PlayerState` - Nouns are ambiguous.
* `Color` - Verb with no context, or ambiguous noun.

#### Functions Returning Bool Should Ask Questions
When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow [the verb rule](#function-verbrule).

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

Good examples:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" is past-tense of "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" when referring to 'previous frame' or 'previous state'.
* `CanReload` - ["Can" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Bad examples:

* `Fire` - Is on fire? Will fire? Do fire?
* `OnFire` - Can be confused with event dispatcher for firing.
* `Dead` - Is dead? Will deaden?
* `Visibility` - Is visible? Set visibility? A description of flying conditions?

#### Event Handlers and Dispatchers Should Start With `On`
Any function that handles an event or dispatches an event should start with `On` and continue to follow [the verb rule](#function-verbrule).

Good examples:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Bad examples:

* `OnData`
* `OnTarget`

**[⬆ Back to Top](#table-of-contents)**
<a name="anc"></a>
<a name="4"></a>

## 4. Asset Naming Conventions
Naming conventions should be treated as law. A project that conforms to a naming convention is able to have its assets managed, searched, parsed, and maintained with incredible ease.

Most things are prefixed with the prefix generally being an acronym of the asset type followed by an underscore.

**Assets use [PascalCase](#cases)**

<a name="base-asset-name"></a>
<a name="4.1"></a>
### 4.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`
All assets should have a _Base Asset Name_. A Base Asset Name represents a logical grouping of related assets. Any asset that is part of this logical group 
should follow the the standard of  `Prefix_BaseAssetName_Variant_Suffix`.

Keeping the pattern `Prefix_BaseAssetName_Variant_Suffix` in mind and using common sense is generally enough to warrant good asset names. Here are some detailed rules regarding each element.

`Prefix` and `Suffix` are to be determined by the asset type through the following [Asset Name Modifier](#asset-name-modifiers) tables.

`BaseAssetName` should be determined by short and easily recognizable name related to the context of this group of assets. For example, if you had a character named Bob, all of Bob's assets would have the `BaseAssetName` of `Bob`.

For unique and specific variations of assets, `Variant` is either a short and easily recognizable name that represents logical grouping of assets that are a subset of an asset's base name. For example, if Bob had multiple skins these skins should still use `Bob` as the `BaseAssetName` but include a recognizable `Variant`. An 'Evil' skin would be referred to as `Bob_Evil` and a 'Retro' skin would be referred to as `Bob_Retro`.

For unique but generic variations of assets, `Variant` is a two digit number starting at `01`. For example, if you have an environment artist generating nondescript rocks, they would be named `Rock_01`, `Rock_02`, `Rock_03`, etc. Except for rare exceptions, you should never require a three digit variant number. If you have more than 100 assets, you should consider organizing them with different base names or using multiple variant names.

Depending on how your asset variants are made, you can chain together variant names. For example, if you are creating flooring assets for an Arch Viz project you should use the base name `Flooring` with chained variants such as `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

<a name="1.1-examples"></a>
#### Examples

##### Character

| Asset Type               | Asset Name   |
| ------------------------ | ------------ |
| Skeletal Mesh            | SK_Bob       |
| Material                 | M_Bob        |
| Texture (Diffuse/Albedo) | T_Bob_D      |
| Texture (Normal)         | T_Bob_N      |
| Texture (Evil Diffuse)   | T_Bob_Evil_D |

##### Prop

| Asset Type               | Asset Name   |
| ------------------------ | ------------ |
| Static Mesh (01)         | SM_Rock_01   |
| Static Mesh (02)         | SM_Rock_02   |
| Static Mesh (03)         | SM_Rock_03   |
| Material                 | M_Rock       |
| Material Instance (Snow) | MI_Rock_Snow |

<a name="asset-name-modifiers"></a>
### 4.2 Asset Name Modifiers

When naming an asset use these tables to determine the prefix and suffix to use with an asset's [Base Asset Name](#base-asset-name).

#### Sections

> 4.2.1 [Most Common](#anc-common)

> 4.2.2 [Animations](#anc-animations)

> 4.2.3 [Artificial Intelligence](#anc-ai)

> 4.2.4 [Prefabs](#anc-prefab)

> 4.2.5 [Materials](#anc-materials)

> 4.2.6 [Textures](#anc-textures)

> 4.2.7 [Miscellaneous](#anc-misc)

> 4.2.8 [Physics](#anc-physics)

> 4.2.9 [Audio](#anc-audio)

> 4.2.10 [User Interface](#anc-ui)

> 4.2.11 [Effects](#anc-effects)

<a name="anc-common"></a>
#### Most Common

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Scene           |  *          |            | [Should be in a folder called Levels.](#levels) e.g. `Levels/A4_C17_Parking_Garage.unity` |
| Level (Persistent)      |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Lighting)        |            | _Lighting  |                                  |
| Level (Geometry)        |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Prefab                  |        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | SM_       |            |                                  |
| Skeletal Mesh           | SK_       |            |                                  |
| Texture                 | T_         | _?         | See [Textures](#anc-textures)    |
| Particle System         | PS_       |            |                                  |

<a name="anc-models"></a>

#### 4.2.1a 3D Models (FBX Files)

PascalCase

| Asset Type    | Prefix | Suffix | Notes |
| ------------- | ------ | ------ | ----- |
| Characters    | CH_    |        |       |
| Vehicles      | VH_    |        |       |
| Weapons       | WP_    |        |       |
| Static Mesh   | SM_    |        |       |
| Skeletal Mesh | SK_    |        |       |
| Skeleton      | SKEL_  |        |       |
| Rig           | RIG_   |        |       |

#### 4.2.1b 3d Models (3ds Max)

All meshes in 3ds Max are lowercase to differentiate them from their FBX export.

| Asset Type    | Prefix | Suffix      | Notes                                   |
| ------------- | ------ | ----------- | --------------------------------------- |
| Mesh          |        | _mesh_lod0* | Only use LOD suffix if model uses LOD's |
| Mesh Collider |        | _collider   |                                         |

<a name="anc-animations"></a>

#### 4.2.2 Animations 
| Asset Type           | Prefix | Suffix | Notes |
| -------------------- | ------ | ------ | ----- |
| Animation Clip       | A_     |        |       |
| Animation Controller | AC_    |        |       |
| Avatar Mask          | AM_    |        |       |
| Morph Target         | MT_    |        |       |

<a name="anc-ai"></a>
#### 4.2.3 Artificial Intelligence

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_     |            |                                  |
| Behavior Tree           | BT_      |            |                                  |
| Blackboard              | BB_       |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_  |            |                                  |
| Environment Query       | EQS_     |            |                                  |
| EnvQueryContext         | EQS_     | Context    |                                  |

<a name="anc-prefab"></a>
#### 4.2.4 Prefabs

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Prefab         |        |            |                                  |
| Prefab Instance         | I       |            |                                  |
| Scriptable Object       |     |        | Assigned "Blueprint" label in Editor |

<a name="anc-materials"></a>

#### 4.2.5 Materials
| Asset Type        | Prefix | Suffix | Notes |
| ----------------- | ------ | ------ | ----- |
| Material          | M_     |        |       |
| Material Instance | MI_    |        |       |
| Physical Material | PM_    |        |       |

<a name="anc-textures"></a>

#### 4.2.6 Textures
| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _AO      |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Packed)        | T_         | _*         | See notes below about [packing](#anc-textures-packing). |
| Texture Cube            | TC_       |            |                                  |
| Media Texture           | MT_       |            |                                  |
| Render Target           | RT_       |            |                                  |
| Cube Render Target      | RTC_     |            |                                  |
| Texture Light Profile   | TLP_     |            |                                  |

<a name="anc-textures-packing"></a>

#### 4.2.6.1 Texture Packing
It is common practice to pack multiple layers of texture data into one texture. An example of this is packing Emissive, Roughness, Ambient Occlusion together as the Red, Green, and Blue channels of a texture respectively. To determine the suffix, simply stack the given suffix letters from above together, e.g. `_ERO`.

> It is generally acceptable to include an Alpha/Opacity layer in your Diffuse/Albedo's alpha channel and as this is common practice, adding `A` to the `_D` suffix is optional.

Packing 4 channels of data into a texture (RGBA) is not recommended except for an Alpha/Opacity mask in the Diffuse/Albedo's alpha channel as a texture with an alpha channel incurs more overhead than one without.
<a name="anc-misc"></a>

#### 4.2.7 Miscellaneous

| Asset Type                      | Prefix | Suffix | Notes |
| ------------------------------- | ------ | ------ | ----- |
| Universal Render Pipeline Asset | URP_   |        |       |
| Post Process Volume Profile     | PP_    |        |       |
| User Interface                  | UI_    |        |       |

<a name="anc-physics"></a>
#### 4.2.8 Physics

| Asset Type        | Prefix | Suffix | Notes |
| ----------------- | ------ | ------ | ----- |
| Physical Material | PM_    |        |       |

<a name="anc-audio"></a>

#### 4.2.9 Audio

| Asset Type     | Prefix | Suffix | Notes                                                        |
| -------------- | ------ | ------ | ------------------------------------------------------------ |
| Audio Clip     | A_     |        |                                                              |
| Audio Mixer    | MIX_   |        |                                                              |
| Dialogue Voice | DV_    |        |                                                              |
| Audio Class    |        |        | No prefix/suffix. Should be put in a folder called AudioClasses |

<a name="anc-ui"></a>
#### 4.2.10 User Interface
| Asset Type       | Prefix | Suffix | Notes |
| ---------------- | ------ | ------ | ----- |
| Font             | Font_  |        |       |
| Texture (Sprite) | T_     | _GUI   |       |

<a name="anc-effects"></a>
#### 4.2.11 Effects
| Asset Type      | Prefix | Suffix | Notes |
| --------------- | ------ | ------ | ----- |
| Particle System | PS_    |        |       |
**[⬆ Back to Top](#table-of-contents)**

<a name="asset-workflows"></a>

## 5. Asset Workflows

This section describes best practices for creating and importing assets usable in Unity.

<a name="toc"></a>
### Sections

> 5.1 [Unity Asset Import Settings](#unityimport)
>
> 5.2 [3ds Max](#3dsmax)
>
> 5.3 [Textures](#textures)
>
> 5.4 [Audio](#audio)

<a name="unityimport"></a>

### 5.1 Unity Asset Import Settings

Unity's [AssetPostprocessor](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) lets you hook into the import pipeline and run scripts prior to or after importing assets. This allows you to enforce import settings when assets are first imported into the project. For example textures that end with `_N` can be marked as a Normal Map on import.

Example guide for Import Settings:

https://github.com/justinwasilenko/Unity-AssetPostProcessor

<a name="3dsmax"></a>
### 5.2 3ds Max

Unity guide on importing from 3ds Max:

https://docs.unity3d.com/2017.4/Documentation/Manual/HOWTO-ImportObjectMax.html

Unity tutorial on the FBX Exporter Package for FBX roundtrip:

https://learn.unity.com/project/3ds-max-to-unity-pipeline

#### Setting up 3ds Max

Unity uses 1 unit = 1 meter. Setup 3ds Max to use Meters by going to ```Customize/Units Setup/System Unit Setup``` and set to 1 Unit = 1 Meter. Using the correct scale is very important for correct Physics / GI / and VR interaction.

Animation frame rate in 3ds Max should be set to 30fps. The ```Time Configuration``` dialog box has 3ds Max's FPS settings

##### Working with Small Objects

* Set ```Customize > Customize User Interface > Mouse Wheel Zoom Increment``` to 0.1m to stop over zooming

* Turn on Viewport Clipping and set the slider on the side of the viewport to be able to zoom in on small meshes. (https://knowledge.autodesk.com/support/3ds-max/learn-explore/caas/sfdcarticles/sfdcarticles/Viewport-Clipping.html)

#### Modeling in 3ds Max

* Follow the [asset naming convention](#anc-models)
* Avoid super long thin triangles (Speeds up tile based renderers & helps with proper GI baking)
* Use Area and Angle Weighted Mesh Normals (Unity Import Setting or Create in 3ds Max)

#### Exporting from 3ds Max into Unity

##### Export Settings:

- Triangulate On
- Tangents and Binormals Off
- Smoothing Groups On
- Preserve edge orientation On
- Units - Automatic Off / Scene Units converted to Meters
- Axis Conversion Z-up

Models created in 3ds Max use a different coordinate system then Unity. Models need to have their pivot point rotated +90 degrees on the X axis to import into Unity correctly.

To do this quickly, open the MaxScript editor, paste this code and select and drag this code on to a Toolbar in 3ds Max to create a button that will run this script. It applies a Xform modifier to rotate the pivot before exporting.

```
fn RotateCreationPivot obj rot =
(
select obj
modPanel.addModToSelection (XForm ()) ui:on
obj.modifiers[#XForm].gizmo.rotation += rot as quat
rotate obj (inverse rot as quat)
)
RotateCreationPivot $ (eulerToQuat(eulerAngles 90 0 0))
```


Script to rotate all objects in 3ds Max scene for export

```
(
    mapped fn ProcessObjectsForUnity node =
    (
        resetxform node
        tm = rotatexmatrix 90
        tm.row4 = node.pos
        node.transform = tm
        node.objectoffsetrot = eulerangles -90 0 0
    )
    
    ProcessObjectsForUnity geometry
)
```

* Batch Exporter for 3ds Max (http://www.strichnet.com/improving-the-fbx-workflow-between-3ds-max-and-unity3d/)

##### Exporting CAT Animation to FBX

Bind normal bones to the CAT rig for use in skinning and exporting

###### Bind Pose

Set Motion Panel/Layer Manager/"Setup/Animation Mode" Toggle to ```Red```
Select only the bones and the mesh you wish to export
Export naming: ModelName.FBX

###### Animation

Set Motion Panel/Layer Manager/"Setup/Animation Mode" to ```Green```
Select ONLY the bones required in your hierarchy (These should match the exact same bones used for Bind Pose), don't include the mesh.
Export naming: ModelName@AnimationName.FBX
The @ symbol is a special Unity naming convention allowing the animation to be bound to the Human.fbx in the Unity editor

#### Importing from 3ds Max into Unity

If importing only animation or bones from a FBX: 

* Set ```Preserve Hierarchy Model``` import option to ```True```
* Set ```Rig > Avatar Definition``` to ```Copy From Other Avatar```

MaxListener Window, set width and height of selected bones, maybe objects too?
$.width = 0.01
$.height = 0.01

**[⬆ Back to Top](#table-of-contents)**

<a name="textures"></a>
### 5.3 Textures

* Textures follow the [naming convention](#anc-textures) found above. 
* They are a power of two (For example, 512 x 512 or 256 x 1024).
* Use Texture Atlases wherever possible.
* 3D software should point to the Unity project textures for consistency when you save or export.
* It is better to resize the texture in Photoshop then to use Unity’s compression options when the in game texture resolution is already known. This reduces the file size and import time of the texture into Unity.
* When working with a high-resolution source PSD outside your Unity project use the same name for both the high-resolution and the imported Unity file. This allows quick iteration when swapping between the 2 textures.

More information for importing textures can be found here: [https://docs.unity3d.com/Manual/ImportingTextures.html](https://docs.unity3d.com/Manual/ImportingTextures.html)

Textures requiring the use of a Alpha channel should follow this guide: [https://docs.unity3d.com/Manual/HOWTO-alphamaps.html](https://docs.unity3d.com/Manual/HOWTO-alphamaps.html)

##### Texture File Format

All textures should be of the .PSD format. No layers should be included and only one Alpha channel in the imported file.

**[⬆ Back to Top](#table-of-contents)**

<a name="audio"></a>
### 5.4 Audio

Only import uncompressed audio files in to Unity using WAV or AIFF formats.

Great guide on [Unity Audio Import Optimization](https://www.gamasutra.com/blogs/ZanderHulme/20190107/333794/Unity_Audio_Import_Optimisation__getting_more_BAM_for_your_RAM.php)

**[⬆ Back to Top](#table-of-contents)**



#### Article References:
https://unity3d.com/learn/tutorials/topics/tips/large-project-organisation
https://github.com/Allar/ue4-style-guide
http://www.arreverie.com/blogs/unity3d-best-practices-folder-structure-source-control/
