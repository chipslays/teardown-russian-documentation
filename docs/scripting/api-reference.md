<h1>
Справочник по API (0.6.2)
</h1>
<h2>
Скриптинг
</h2>
<p>
В качестве языка сценариев Teardown использует Lua версии 5.1. Lua 5.1
справочное руководство можно найти
<a href="https://www.lua.org/manual/5.1/">здесь</a>. Каждый скрипт Teardown
работает в собственном контексте Lua и может взаимодействовать только с движком и
другими скриптами через функции API и реестр. Реестр - это
база данных иерархических глобальных переменных, которая используется как внутри
в движка для связи между скриптами так и как способ хранить
постоянные данные.
<p>
API Teardown использует только собственные типы Lua. Дескрипторы объектов - это простые числа Lua. Векторные типы представлены в виде простых таблиц Lua и так далее. Каждый скрипт имеет четыре функции обратного вызова.
<p>
<table border=0><tr><td class='header'>
 Function 
</td><td class='header'>
 Описание
</td></tr>
<tr><td class='first' valign='top'>
function `init()`
</td><td valign='top'> 
Вызывается один раз во время загрузки
</td></tr><tr><td class='first' valign='top'>
function `tick(dt)`
</td><td valign='top'> 
Вызывается ровно один раз за кадр. Временной шаг может меняться, но всегда
от 0,0 до 0,0333333
</td></tr><tr><td class='first' valign='top'>
function `update(dt)`
</td><td valign='top'> 
Вызывается с фиксированной частотой обновления, но не более двух раз за кадр. Временной шаг всегда 0,0166667 (60 обновлений в секунду). В зависимости от частоты кадров он может вообще не вызываться для определенного кадра.
</td></tr><tr><td class='first' valign='top'>
function `draw()`
</td><td valign='top'> 
Вызывается при отрисовке 2D-оверлея после сцены, но до стандартного HUD. Функции пользовательского интерфейса можно использовать только из этого обратного вызова.
</td></tr><table/>
<p>
<p>

<p>
<hr/>
<h2>
Параметры
</h2>
<p>
Скрипты могут иметь параметры, определенные в файле XML. Они служат
в качестве входных данных для конкретного экземпляра скрипта и может использоваться для
настройки различных опций и параметров скрипта. Пока эти
параметры можно прочитать в любой момент в скрипте, рекомендуется
скопировать их в глобальную переменную внутри или вне функции `init()`.
<p>

<p>
<a href='#GetIntParam'>GetIntParam</a></br>
<a href='#GetFloatParam'>GetFloatParam</a></br>
<a href='#GetBoolParam'>GetBoolParam</a></br>
<a href='#GetStringParam'>GetStringParam</a></br>
<hr/>
<h2>
Управление скриптом
</h2>
<p>
Общие функции, управляющие работой и выполнением скрипта.
<table border=0><tr><td class='header'>
 Идентификатор клавиши
</td><td class='header'>
 Описание
</td></tr>
<tr><td class='first' valign='top'>
esc
</td><td valign='top'> 
Клавиша Escape
</td></tr><tr><td class='first' valign='top'>
lmb
</td><td valign='top'> 
Левая кнопка мыши
</td></tr><tr><td class='first' valign='top'>
rmb
</td><td valign='top'> 
Правая кнопка мыши
</td></tr><tr><td class='first' valign='top'>
up
</td><td valign='top'> 
Стрелка вверх
</td></tr><tr><td class='first' valign='top'>
down
</td><td valign='top'> 
Стрелка вниз
</td></tr><tr><td class='first' valign='top'>
left
</td><td valign='top'> 
Стрелка влево
</td></tr><tr><td class='first' valign='top'>
right
</td><td valign='top'> 
Стрелка вправо
</td></tr><tr><td class='first' valign='top'>
space
</td><td valign='top'> 
Пробел
</td></tr><tr><td class='first' valign='top'>
shift
</td><td valign='top'> 
Клавиша Shift
</td></tr><tr><td class='first' valign='top'>
ctrl
</td><td valign='top'> 
Клавиша Ctrl
</td></tr><tr><td class='first' valign='top'>
interact
</td><td valign='top'> 
Клавиша взаимодействия
</td></tr><tr><td class='first' valign='top'>
return
</td><td valign='top'> 
Клавиша return
</td></tr><tr><td class='first' valign='top'>
any
</td><td valign='top'> 
Любая клавиша или кнопка мыши
</td></tr><tr><td class='first' valign='top'>
a,b,c,...
</td><td valign='top'> 
Латинские, буквенные клавиши от A до Z
</td></tr><tr><td class='first' valign='top'>
mousewheel
</td><td valign='top'> 
Колесико мыши. Действует только в `InputValue`.
</td></tr><tr><td class='first' valign='top'>
mousedx
</td><td valign='top'> 
Разница по горизонтали с мышью. Действует только в `InputValue`.
</td></tr><tr><td class='first' valign='top'>
mousedy
</td><td valign='top'> 
Разница по верктикали с мышью. Действует только в `InputValue`.
</td></tr><table/>
<p>

<p>
<a href='#GetVersion'>GetVersion</a></br>
<a href='#HasVersion'>HasVersion</a></br>
<a href='#GetTime'>GetTime</a></br>
<a href='#GetTimeStep'>GetTimeStep</a></br>
<a href='#InputPressed'>InputPressed</a></br>
<a href='#InputReleased'>InputReleased</a></br>
<a href='#InputDown'>InputDown</a></br>
<a href='#InputValue'>InputValue</a></br>
<a href='#SetValue'>SetValue</a></br>
<a href='#StartLevel'>StartLevel</a></br>
<a href='#SetPaused'>SetPaused</a></br>
<a href='#Restart'>Restart</a></br> <a href='#Menu'>Menu</a></br>
<hr/>
<h2>
Реестр (Registry)
</h2>
<p>
Механизм Teardown использует глобальный реестр пар ключ/значение, который скрипты могут читать и записывать. Движок предоставляет большой объем внутренней информации через реестр, но его также можно использовать как способ взаимодействия скриптов друг с другом.
<p>
Реестр представляет собой иерархическую структуру узлов (node) и может хранить значение в каждом узле (родительские узлы также могут иметь значение). Значения могут быть числами с плавающей запятой, целыми, логическими или строковыми, но все типы автоматически преобразуются, если запрашивается другой тип. 

Некоторые узлы реестра зарезервированы и используются для специальных целей.

<table border=0><tr><td class='header'>
 Ключ
</td><td class='header'>
 Описание
</td></tr>
<tr><td class='first' valign='top'>
options
</td><td valign='top'> 
зарезервировано для настроек игры (защита от записи для модов)
</td></tr><tr><td class='first' valign='top'>
game
</td><td valign='top'> 
зарезервировано для внутреннего устройства игрового движка (см. документацию)
</td></tr><tr><td class='first' valign='top'>
savegame
</td><td valign='top'> 
используется для постоянных игровых данных (защита от записи для модов)
</td></tr><tr><td class='first' valign='top'>
savegame.mod
</td><td valign='top'> 
используется для постоянных данных мода
</td></tr><tr><td class='first' valign='top'>
level
</td><td valign='top'> 
не зарезервировано, но рекомендуется для конкретных уровней записей и взаимодействия скриптов
</td></tr><table/>
<p>

<p>
<a href='#ClearKey'>ClearKey</a></br>
<a href='#ListKeys'>ListKeys</a></br> <a href='#HasKey'>HasKey</a></br>
<a href='#SetInt'>SetInt</a></br> <a href='#GetInt'>GetInt</a></br>
<a href='#SetFloat'>SetFloat</a></br>
<a href='#GetFloat'>GetFloat</a></br>
<a href='#SetBool'>SetBool</a></br> <a href='#GetBool'>GetBool</a></br>
<a href='#SetString'>SetString</a></br>
<a href='#GetString'>GetString</a></br>
<hr/>
<h2>
Векторная математика (Vector math)
</h2>
<p>
Векторная математика используется в сценариях Teardown для представления трехмерных положений (3D positions), направлений (directions), поворотов (rotations) и преобразований (transforms). Базовые типы - это векторы, кватернионы и преобразования. Векторы и кватернионы представляют собой индексированные таблицы с тремя и четырьмя компонентами. Преобразования - это таблицы, состоящие из одного вектора (pos) и одного кватерниона (rot)
<p>

<p>
<a href='#Vec'>Vec</a></br> <a href='#VecCopy'>VecCopy</a></br>
<a href='#VecLength'>VecLength</a></br>
<a href='#VecNormalize'>VecNormalize</a></br>
<a href='#VecScale'>VecScale</a></br> <a href='#VecAdd'>VecAdd</a></br>
<a href='#VecSub'>VecSub</a></br> <a href='#VecDot'>VecDot</a></br>
<a href='#VecCross'>VecCross</a></br>
<a href='#VecLerp'>VecLerp</a></br> <a href='#Quat'>Quat</a></br>
<a href='#QuatCopy'>QuatCopy</a></br>
<a href='#QuatAxisAngle'>QuatAxisAngle</a></br>
<a href='#QuatEuler'>QuatEuler</a></br>
<a href='#QuatLookAt'>QuatLookAt</a></br>
<a href='#QuatSlerp'>QuatSlerp</a></br>
<a href='#QuatRotateQuat'>QuatRotateQuat</a></br>
<a href='#Transform'>Transform</a></br>
<a href='#TransformCopy'>TransformCopy</a></br>
<a href='#TransformToParentTransform'>TransformToParentTransform</a></br>
<a href='#TransformToLocalTransform'>TransformToLocalTransform</a></br>
<a href='#TransformToParentVec'>TransformToParentVec</a></br>
<a href='#TransformToLocalVec'>TransformToLocalVec</a></br>
<a href='#TransformToParentPoint'>TransformToParentPoint</a></br>
<a href='#TransformToLocalPoint'>TransformToLocalPoint</a></br>
<hr/>
<h2>
Сущность (Entity)
</h2>
<p>
Сущность является основой большинства объектов в движке Teardown (тела, формы, источники света, местоположения и т. д.). Все сущности могут иметь теги, которые предназначены для хранения настраиваемых свойств сущностей для скриптов. Некоторые теги также зарезервированы для использования в движке. Подробности см. в документации.
<p>

<p>
<a href='#SetTag'>SetTag</a></br>
<a href='#RemoveTag'>RemoveTag</a></br>
<a href='#HasTag'>HasTag</a></br>
<a href='#GetTagValue'>GetTagValue</a></br>
<a href='#GetDescription'>GetDescription</a></br>
<a href='#SetDescription'>SetDescription</a></br>
<a href='#Delete'>Delete</a></br>
<a href='#IsHandleValid'>IsHandleValid</a></br>
<hr/>
<h2>
Тело (Body)
</h2>
<p>
Тело представляет собой твердое тело на сцене. Он может быть как статическим, так и динамическим. Физика влияет только на динамические тела.
<p>

<p>
<a href='#FindBody'>FindBody</a></br>
<a href='#FindBodies'>FindBodies</a></br>
<a href='#GetBodyTransform'>GetBodyTransform</a></br>
<a href='#SetBodyTransform'>SetBodyTransform</a></br>
<a href='#GetBodyMass'>GetBodyMass</a></br>
<a href='#IsBodyDynamic'>IsBodyDynamic</a></br>
<a href='#SetBodyDynamic'>SetBodyDynamic</a></br>
<a href='#SetBodyVelocity'>SetBodyVelocity</a></br>
<a href='#GetBodyVelocity'>GetBodyVelocity</a></br>
<a href='#GetBodyVelocityAtPos'>GetBodyVelocityAtPos</a></br>
<a href='#SetBodyAngularVelocity'>SetBodyAngularVelocity</a></br>
<a href='#GetBodyAngularVelocity'>GetBodyAngularVelocity</a></br>
<a href='#IsBodyActive'>IsBodyActive</a></br>
<a href='#ApplyBodyImpulse'>ApplyBodyImpulse</a></br>
<a href='#GetBodyShapes'>GetBodyShapes</a></br>
<a href='#GetBodyVehicle'>GetBodyVehicle</a></br>
<a href='#GetBodyBounds'>GetBodyBounds</a></br>
<a href='#GetBodyCenterOfMass'>GetBodyCenterOfMass</a></br>
<a href='#IsBodyVisible'>IsBodyVisible</a></br>
<a href='#IsBodyBroken'>IsBodyBroken</a></br>
<a href='#IsBodyJointedToStatic'>IsBodyJointedToStatic</a></br>
<a href='#DrawBodyOutline'>DrawBodyOutline</a></br>
<a href='#DrawBodyHighlight'>DrawBodyHighlight</a></br>
<hr/>
<h2>
Форма (Shape)
</h2>
<p>
Фигура - это воксельный объект, который всегда принадлежит телу. Одно тело может содержать несколько форм. Преобразование формы выражается в системе координат родительского тела.
<p>

<p>
<a href='#FindShape'>FindShape</a></br>
<a href='#FindShapes'>FindShapes</a></br>
<a href='#GetShapeLocalTransform'>GetShapeLocalTransform</a></br>
<a href='#SetShapeLocalTransform'>SetShapeLocalTransform</a></br>
<a href='#GetShapeWorldTransform'>GetShapeWorldTransform</a></br>
<a href='#GetShapeBody'>GetShapeBody</a></br>
<a href='#GetShapeJoints'>GetShapeJoints</a></br>
<a href='#GetShapeLights'>GetShapeLights</a></br>
<a href='#GetShapeBounds'>GetShapeBounds</a></br>
<a href='#SetShapeEmissiveScale'>SetShapeEmissiveScale</a></br>
<a href='#GetShapeMaterialAtPosition'>GetShapeMaterialAtPosition</a></br>
<a href='#GetShapeSize'>GetShapeSize</a></br>
<a href='#GetShapeVoxelCount'>GetShapeVoxelCount</a></br>
<a href='#IsShapeVisible'>IsShapeVisible</a></br>
<a href='#IsShapeBroken'>IsShapeBroken</a></br>
<a href='#DrawShapeOutline'>DrawShapeOutline</a></br>
<a href='#DrawShapeHighlight'>DrawShapeHighlight</a></br>
<hr/>
<h2>
Положение (Location)
</h2>
<p>
Положение - это трансформации, помещаемые в редакторе в виде маркеров. Преобразования местоположения всегда выражаются в координатах мирового пространства.
<p>

<p>
<a href='#FindLocation'>FindLocation</a></br>
<a href='#FindLocations'>FindLocations</a></br>
<a href='#GetLocationTransform'>GetLocationTransform</a></br>
<hr/>
<h2>
Соединение (Joint)
</h2>
<p>
Соединения используются для физического соединения двух фигур. Есть несколько типов соединений, и они обычно размещаются в редакторе. Когда происходит разрушение, соединения могут приобретать новую форму, отсоединяться или полностью отключаться.
<p>

<p>
<a href='#FindJoint'>FindJoint</a></br>
<a href='#FindJoints'>FindJoints</a></br>
<a href='#IsJointBroken'>IsJointBroken</a></br>
<a href='#GetJointType'>GetJointType</a></br>
<a href='#GetJointOtherShape'>GetJointOtherShape</a></br>
<a href='#SetJointMotor'>SetJointMotor</a></br>
<a href='#SetJointMotorTarget'>SetJointMotorTarget</a></br>
<a href='#GetJointLimits'>GetJointLimits</a></br>
<a href='#GetJointMovement'>GetJointMovement</a></br>
<hr/>
<h2>
Освещение (Light)
</h2>
<p>
Источники света могут быть нескольких типов и настраиваться в редакторе. Если источник света принадлежит фигуре, интенсивность источника света масштабируется по шкале излучения этой формы. Если исходная форма ломается, шкала излучения устанавливается на ноль, а источник света отключается. Источник света без родительской формы всегда будет излучать свет, если он явно не отключен скриптом.
<p>

<p>
<a href='#FindLight'>FindLight</a></br>
<a href='#FindLights'>FindLights</a></br>
<a href='#SetLightEnabled'>SetLightEnabled</a></br>
<a href='#SetLightColor'>SetLightColor</a></br>
<a href='#SetLightIntensity'>SetLightIntensity</a></br>
<a href='#GetLightTransform'>GetLightTransform</a></br>
<a href='#GetLightShape'>GetLightShape</a></br>
<a href='#IsPointAffectedByLight'>IsPointAffectedByLight</a></br>
<hr/>
<h2>
Триггер (Trigger)
</h2>
<p>
Триггеры могут быть размещены в сцене и опрошены скриптами, чтобы увидеть, находится ли что-то в определенной части сцены.
<p>

<p>
<a href='#FindTrigger'>FindTrigger</a></br>
<a href='#FindTriggers'>FindTriggers</a></br>
<a href='#GetTriggerTransform'>GetTriggerTransform</a></br>
<a href='#SetTriggerTransform'>SetTriggerTransform</a></br>
<a href='#IsBodyInTrigger'>IsBodyInTrigger</a></br>
<a href='#IsVehicleInTrigger'>IsVehicleInTrigger</a></br>
<a href='#IsShapeInTrigger'>IsShapeInTrigger</a></br>
<a href='#IsPointInTrigger'>IsPointInTrigger</a></br>
<a href='#IsTriggerEmpty'>IsTriggerEmpty</a></br>
<hr/>
<h2>
Экран (Screen)
</h2>
<p>
На экранах отображается содержимое сценариев пользовательского интерфейса, и их можно сделать интерактивными.
<p>

<p>
<a href='#FindScreen'>FindScreen</a></br>
<a href='#FindScreens'>FindScreens</a></br>
<a href='#SetScreenEnabled'>SetScreenEnabled</a></br>
<a href='#IsScreenEnabled'>IsScreenEnabled</a></br>
<a href='#GetScreenShape'>GetScreenShape</a></br>
<hr/>
<h2>
Транспорт (Vehicle)
</h2>
<p>
Транспортные средства настраиваются в редакторе и состоят из нескольких частей, принадлежащих объекту транспортного средства.
<p>

<p>
<a href='#FindVehicle'>FindVehicle</a></br>
<a href='#FindVehicles'>FindVehicles</a></br>
<a href='#GetVehicleTransform'>GetVehicleTransform</a></br>
<a href='#GetVehicleBody'>GetVehicleBody</a></br>
<a href='#GetVehicleHealth'>GetVehicleHealth</a></br>
<a href='#GetVehicleDriverPos'>GetVehicleDriverPos</a></br>
<a href='#DriveVehicle'>DriveVehicle</a></br>
<hr/>
<h2>
Игрок (Player)
</h2>
<p>
Функции игрока предоставляют определенную информацию о нем.
<p>

<p>
<a href='#GetPlayerPos'>GetPlayerPos</a></br>
<a href='#GetPlayerTransform'>GetPlayerTransform</a></br>
<a href='#SetPlayerTransform'>SetPlayerTransform</a></br>
<a href='#GetPlayerCameraTransform'>GetPlayerCameraTransform</a></br>
<a href='#SetPlayerSpawnTransform'>SetPlayerSpawnTransform</a></br>
<a href='#GetPlayerVelocity'>GetPlayerVelocity</a></br>
<a href='#SetPlayerVehicle'>SetPlayerVehicle</a></br>
<a href='#SetPlayerVelocity'>SetPlayerVelocity</a></br>
<a href='#GetPlayerVehicle'>GetPlayerVehicle</a></br>
<a href='#GetPlayerGrabShape'>GetPlayerGrabShape</a></br>
<a href='#GetPlayerGrabBody'>GetPlayerGrabBody</a></br>
<a href='#GetPlayerPickShape'>GetPlayerPickShape</a></br>
<a href='#GetPlayerPickBody'>GetPlayerPickBody</a></br>
<a href='#GetPlayerInteractShape'>GetPlayerInteractShape</a></br>
<a href='#GetPlayerInteractBody'>GetPlayerInteractBody</a></br>
<a href='#SetPlayerScreen'>SetPlayerScreen</a></br>
<a href='#GetPlayerScreen'>GetPlayerScreen</a></br>
<a href='#SetPlayerHealth'>SetPlayerHealth</a></br>
<a href='#GetPlayerHealth'>GetPlayerHealth</a></br>
<a href='#RespawnPlayer'>RespawnPlayer</a></br>
<a href='#RegisterTool'>RegisterTool</a></br>
<a href='#GetToolBody'>GetToolBody</a></br>
<a href='#SetToolTransform'>SetToolTransform</a></br>
<hr/>
<h2>
Звук (Sound)
</h2>
<p>
Звуковые функции используются для воспроизведения звуков или лупов в мире. Функции звука установлены всегда, и на них влияет акустическое моделирование. Если вы хотите проигрывать «сухие» звуки без акустики, вам следует использовать `UiSound` и `UiSoundLoop` в разделе «Пользовательский интерфейс».
<p>

<p>
<a href='#LoadSound'>LoadSound</a></br>
<a href='#LoadLoop'>LoadLoop</a></br>
<a href='#PlaySound'>PlaySound</a></br>
<a href='#PlayLoop'>PlayLoop</a></br>
<a href='#PlayMusic'>PlayMusic</a></br>
<a href='#StopMusic'>StopMusic</a></br>
<hr/>
<h2>
Спрайт (Sprite)
</h2>
<p>
Спрайты - это 2D-изображения в формате PNG или JPG, которые можно размещать в мире. Спрайты можно рисовать как с тестом глубины, так и без него (закрытые геометрией). На спрайты не влияет освещение, но они проходят постобработку. Если вы хотите отображать позиционированную информацию для игрока в виде наложения, вы, вероятно, захотите вместо этого использовать функции пользовательского интерфейса в сочетании с `UiWorldToPixel`. 
<p>

<p>
<a href='#LoadSprite'>LoadSprite</a></br>
<a href='#DrawSprite'>DrawSprite</a></br>
<hr/>
<h2>
Запросы сцены (Scene queries)
</h2>
<p>
Запрашивайте уровень различными способами.
<p>

<p>
<a href='#QueryRequire'>QueryRequire</a></br>
<a href='#QueryRejectVehicle'>QueryRejectVehicle</a></br>
<a href='#QueryRejectBody'>QueryRejectBody</a></br>
<a href='#QueryRejectShape'>QueryRejectShape</a></br>
<a href='#QueryRaycast'>QueryRaycast</a></br>
<a href='#QueryClosestPoint'>QueryClosestPoint</a></br>
<a href='#QueryAabbShapes'>QueryAabbShapes</a></br>
<a href='#QueryAabbBodies'>QueryAabbBodies</a></br>
<a href='#GetLastSound'>GetLastSound</a></br>
<a href='#IsPointInWater'>IsPointInWater</a></br>
<hr/>
<h2>
Разное (Miscellaneous)
</h2>
<p>
Функции периферийного характера, которые больше нигде не подходят.
<p>

<p>
<a href='#Shoot'>Shoot</a></br> <a href='#MakeHole'>MakeHole</a></br>
<a href='#Explosion'>Explosion</a></br>
<a href='#SpawnParticle'>SpawnParticle</a></br>
<a href='#SpawnFire'>SpawnFire</a></br>
<a href='#GetFireCount'>GetFireCount</a></br>
<a href='#GetCameraTransform'>GetCameraTransform</a></br>
<a href='#SetCameraTransform'>SetCameraTransform</a></br>
<a href='#PointLight'>PointLight</a></br>
<a href='#SetTimeScale'>SetTimeScale</a></br>
<a href='#DrawLine'>DrawLine</a></br>
<a href='#DebugLine'>DebugLine</a></br>
<a href='#DebugCross'>DebugCross</a></br>
<a href='#DebugWatch'>DebugWatch</a></br>
<a href='#DebugPrint'>DebugPrint</a></br>
<hr/>
<h2>
Пользовательский интерфейс (User Interface)
</h2>
<p>
Функции пользовательского интерфейса используются для рисования интерактивной 2D-графики и могут быть вызваны только из функции рисования скрипта. Функции пользовательского интерфейса разработаны с учетом парадигмы GUI немедленного режима и используют курсор и стек состояний. Нажатие и выталкивание стека дешево и предназначено для частого вызова.
<p>

<p>
<a href='#UiMakeInteractive'>UiMakeInteractive</a></br>
<a href='#UiPush'>UiPush</a></br> <a href='#UiPop'>UiPop</a></br>
<a href='#UiWidth'>UiWidth</a></br>
<a href='#UiHeight'>UiHeight</a></br>
<a href='#UiCenter'>UiCenter</a></br>
<a href='#UiMiddle'>UiMiddle</a></br>
<a href='#UiColor'>UiColor</a></br>
<a href='#UiColorFilter'>UiColorFilter</a></br>
<a href='#UiTranslate'>UiTranslate</a></br>
<a href='#UiRotate'>UiRotate</a></br>
<a href='#UiScale'>UiScale</a></br>
<a href='#UiWindow'>UiWindow</a></br>
<a href='#UiSafeMargins'>UiSafeMargins</a></br>
<a href='#UiAlign'>UiAlign</a></br>
<a href='#UiModalBegin'>UiModalBegin</a></br>
<a href='#UiModalEnd'>UiModalEnd</a></br>
<a href='#UiDisableInput'>UiDisableInput</a></br>
<a href='#UiEnableInput'>UiEnableInput</a></br>
<a href='#UiReceivesInput'>UiReceivesInput</a></br>
<a href='#UiGetMousePos'>UiGetMousePos</a></br>
<a href='#UiIsMouseInRect'>UiIsMouseInRect</a></br>
<a href='#UiWorldToPixel'>UiWorldToPixel</a></br>
<a href='#UiPixelToWorld'>UiPixelToWorld</a></br>
<a href='#UiBlur'>UiBlur</a></br> <a href='#UiFont'>UiFont</a></br>
<a href='#UiFontHeight'>UiFontHeight</a></br>
<a href='#UiText'>UiText</a></br>
<a href='#UiGetTextSize'>UiGetTextSize</a></br>
<a href='#UiWordWrap'>UiWordWrap</a></br>
<a href='#UiTextOutline'>UiTextOutline</a></br>
<a href='#UiTextShadow'>UiTextShadow</a></br>
<a href='#UiRect'>UiRect</a></br> <a href='#UiImage'>UiImage</a></br>
<a href='#UiGetImageSize'>UiGetImageSize</a></br>
<a href='#UiImageBox'>UiImageBox</a></br>
<a href='#UiSound'>UiSound</a></br>
<a href='#UiSoundLoop'>UiSoundLoop</a></br>
<a href='#UiMute'>UiMute</a></br>
<a href='#UiButtonImageBox'>UiButtonImageBox</a></br>
<a href='#UiButtonHoverColor'>UiButtonHoverColor</a></br>
<a href='#UiButtonPressColor'>UiButtonPressColor</a></br>
<a href='#UiButtonPressDist'>UiButtonPressDist</a></br>
<a href='#UiTextButton'>UiTextButton</a></br>
<a href='#UiImageButton'>UiImageButton</a></br>
<a href='#UiBlankButton'>UiBlankButton</a></br>
<a href='#UiSlider'>UiSlider</a></br>
<a href='#UiGetScreen'>UiGetScreen</a></br>
<hr/>
<a name='GetIntParam'></a>
<h3 class='function'>
GetIntParam
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetIntParam(<span class='argname'>name, default</span>)</pre>
<p>
Аргументы<br/> <span class="argname">name</span> <span
class="argtype">(string)</span> – Имя параметра<br/> <span
class="argname">default</span> <span class="argtype">(number)</span> –
Значение параметра по умолчанию<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(number)</span> – Значение параметра<br/>
<p><p>
</p>
<pre class='example'>
--Retrieve blinkcount parameter, or set to 5 if omitted
parameterBlinkCount = GetIntParameter("blinkcount", 5)

</pre>
<hr/>
<a name='GetFloatParam'></a>
<h3 class='function'>
GetFloatParam
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetFloatParam(<span class='argname'>name, default</span>)</pre>
<p>
Аргументы<br/> <span class="argname">name</span> <span
class="argtype">(string)</span> – Имя параметра<br/> <span
class="argname">default</span> <span class="argtype">(number)</span> –
Значение параметра по умолчанию<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(number)</span> – Значение параметра<br/>
<p><p>
</p>
<pre class='example'>
--Retrieve speed parameter, or set to 10.0 if omitted
parameterSpeed = GetFloatParameter("speed", 10.0)

</pre>
<hr/>
<a name='GetBoolParam'></a>
<h3 class='function'>
GetBoolParam
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetBoolParam(<span class='argname'>name, default</span>)</pre>
<p>
Аргументы<br/> <span class="argname">name</span> <span
class="argtype">(string)</span> – Имя параметра<br/> <span
class="argname">default</span> <span class="argtype">(boolean)</span> –
Значение параметра по умолчанию<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(boolean)</span> – Значение параметра<br/>
<p><p>
</p>
<pre class='example'>
--Retrieve playsound parameter, or false if omitted
parameterPlaySound = GetBoolParameter("playsound", false)

</pre>
<hr/>
<a name='GetStringParam'></a>
<h3 class='function'>
GetStringParam
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetStringParam(<span class='argname'>name, default</span>)</pre>
<p>
Аргументы<br/> <span class="argname">name</span> <span
class="argtype">(string)</span> – Имя параметра<br/> <span
class="argname">default</span> <span class="argtype">(string)</span> –
Значение параметра по умолчанию<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(string)</span> – Значение параметра<br/>
<p><p>
</p>
<pre class='example'>
--Retrieve mode parameter, or "idle" if omitted
parameterMode = GetSrtingParameter("mode", "idle")

</pre>
<hr/>
<a name='GetVersion'></a>
<h3 class='function'>
GetVersion
</h3>
<pre class='funcdef'><span class='retname'>version = </span>GetVersion(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">version</span> <span
class="argtype">(string)</span> – Dot separated string of current
version of the game<br/>
<p><p>
</p>
<pre class='example'>
local v = GetVersion()
--v is "0.5.0"

</pre>
<hr/>
<a name='HasVersion'></a>
<h3 class='function'>
HasVersion
</h3>
<pre class='funcdef'><span class='retname'>match = </span>HasVersion(<span class='argname'>version</span>)</pre>
<p>
Аргументы<br/> <span class="argname">version</span> <span
class="argtype">(string)</span> – Reference version<br/>
<p>
Возвращаемое значение<br/> <span class="retname">match</span> <span
class="argtype">(boolean)</span> – True if current version is at least
provided one<br/>
<p><p>
</p>
<pre class='example'>
if HasVersion("0.6.0") then
    --conditional code that only works on 0.6.0 or above
else
    --legacy code that works on earlier versions
end

</pre>
<hr/>
<a name='GetTime'></a>
<h3 class='function'>
GetTime
</h3>
<pre class='funcdef'><span class='retname'>time = </span>GetTime(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">time</span> <span
class="argtype">(number)</span> – The time in seconds since level was
started<br/>
<p>
Returns running time of this script. If called from update, this returns
the simulated time, otherwise it returns wall time.
<p>
</p>
<pre class='example'>
local t = GetTime()

</pre>
<hr/>
<a name='GetTimeStep'></a>
<h3 class='function'>
GetTimeStep
</h3>
<pre class='funcdef'><span class='retname'>dt = </span>GetTimeStep(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">dt</span> <span
class="argtype">(number)</span> – The timestep in seconds<br/>
<p>
Returns timestep of the last frame. If called from update, this returns
the simulation time step, which is always one 60th of a second
(0.0166667). If called from tick or draw it returns the actual time
since last frame.
<p>
</p>
<pre class='example'>
local dt = GetTimeStep()

</pre>
<hr/>
<a name='InputPressed'></a>
<h3 class='function'>
InputPressed
</h3>
<pre class='funcdef'><span class='retname'>pressed = </span>InputPressed(<span class='argname'>input</span>)</pre>
<p>
Аргументы<br/> <span class="argname">input</span> <span
class="argtype">(string)</span> – The input identifier<br/>
<p>
Возвращаемое значение<br/> <span class="retname">pressed</span> <span
class="argtype">(boolean)</span> – True if input was pressed during last
frame<br/>
<p><p>
</p>
<pre class='example'>
if InputPressed("interact") then
    ...
end

</pre>
<hr/>
<a name='InputReleased'></a>
<h3 class='function'>
InputReleased
</h3>
<pre class='funcdef'><span class='retname'>pressed = </span>InputReleased(<span class='argname'>input</span>)</pre>
<p>
Аргументы<br/> <span class="argname">input</span> <span
class="argtype">(string)</span> – The input identifier<br/>
<p>
Возвращаемое значение<br/> <span class="retname">pressed</span> <span
class="argtype">(boolean)</span> – True if input was released during
last frame<br/>
<p><p>
</p>
<pre class='example'>
if InputReleased("interact") then
    ...
end

</pre>
<hr/>
<a name='InputDown'></a>
<h3 class='function'>
InputDown
</h3>
<pre class='funcdef'><span class='retname'>pressed = </span>InputDown(<span class='argname'>input</span>)</pre>
<p>
Аргументы<br/> <span class="argname">input</span> <span
class="argtype">(string)</span> – The input identifier<br/>
<p>
Возвращаемое значение<br/> <span class="retname">pressed</span> <span
class="argtype">(boolean)</span> – True if input is currently held
down<br/>
<p><p>
</p>
<pre class='example'>
if InputDown("interact") then
...
end

</pre>
<hr/>
<a name='InputValue'></a>
<h3 class='function'>
InputValue
</h3>
<pre class='funcdef'><span class='retname'>value = </span>InputValue(<span class='argname'>input</span>)</pre>
<p>
Аргументы<br/> <span class="argname">input</span> <span
class="argtype">(string)</span> – The input identifier<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(number)</span> – Depends on input type<br/>
<p><p>
</p>
<pre class='example'>
scrollPos = scrollPos + InputValue("mousewheel")

</pre>
<hr/>
<a name='SetValue'></a>
<h3 class='function'>
SetValue
</h3>
<pre class='funcdef'><span class='retname'></span>SetValue(<span class='argname'>variable, value, [transition], [time]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">variable</span> <span
class="argtype">(string)</span> – Name of number variable in the global
context<br/> <span class="argname">value</span> <span
class="argtype">(number)</span> – The new value<br/> <span
class="argname">transition</span> <span class="argtype">(string,
optional)</span> – Transition type. See description.<br/> <span
class="argname">time</span> <span class="argtype">(number,
optional)</span> – Transition time (seconds)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Set value of a number variable in the global context with an optional
transition. If a transition is provided the value will animate from
current value to the new value during the transition time. Transition
can be one of the following:
<table border=0><tr><td class='header'>
 Transition 
</td><td class='header'>
 Описание
</td></tr>
<tr><td class='first' valign='top'>
linear
</td><td valign='top'> 
Linear transition
</td></tr><tr><td class='first' valign='top'>
cosine
</td><td valign='top'> 
Slow at beginning and end
</td></tr><tr><td class='first' valign='top'>
easein
</td><td valign='top'> 
Slow at beginning
</td></tr><tr><td class='first' valign='top'>
easeout
</td><td valign='top'> 
Slow at end
</td></tr><tr><td class='first' valign='top'>
bounce
</td><td valign='top'> 
Bounce and overshoot new value
</td></tr><table/>
<p>
</p>
<pre class='example'>
myValue = 0
SetValue("myValue", 1, "linear", 0.5)

This will change the value of myValue from 0 to 1 in a linear fasion over 0.5 seconds

</pre>
<hr/>
<a name='StartLevel'></a>
<h3 class='function'>
StartLevel
</h3>
<pre class='funcdef'><span class='retname'></span>StartLevel(<span class='argname'>mission, path, [layers]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">mission</span> <span
class="argtype">(string)</span> – An identifier of your choice<br/>
<span class="argname">path</span> <span class="argtype">(string)</span>
– Path to level XML file<br/> <span class="argname">layers</span> <span
class="argtype">(string, optional)</span> – Active layers. Default is no
layers.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Start a level
<p>
</p>
<pre class='example'>
--Start level with no active layers
StartLevel("level1", "MOD/level1.xml")

--Start level with two layers
StartLevel("level1", "MOD/level1.xml", "vehicles targets")

</pre>
<hr/>
<a name='SetPaused'></a>
<h3 class='function'>
SetPaused
</h3>
<pre class='funcdef'><span class='retname'></span>SetPaused(<span class='argname'>paused</span>)</pre>
<p>
Аргументы<br/> <span class="argname">paused</span> <span
class="argtype">(boolean)</span> – True if game should be paused<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Set paused state of the game
<p>
</p>
<pre class='example'>
--Pause game and bring up pause menu on HUD
SetPaused(true)

</pre>
<hr/>
<a name='Restart'></a>
<h3 class='function'>
Restart
</h3>
<pre class='funcdef'><span class='retname'></span>Restart(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Restart level
<p>
</p>
<pre class='example'>
if shouldRestart then
Restart()
end

</pre>
<hr/>
<a name='Menu'></a>
<h3 class='function'>
Menu
</h3>
<pre class='funcdef'><span class='retname'></span>Menu(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Go to main menu
<p>
</p>
<pre class='example'>
if shouldExitLevel then
Menu()
end

</pre>
<hr/>
<a name='ClearKey'></a>
<h3 class='function'>
ClearKey
</h3>
<pre class='funcdef'><span class='retname'></span>ClearKey(<span class='argname'>key</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key to clear<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Remove registry node, including all child nodes.
<p>
</p>
<pre class='example'>
--If the registry looks like this:
--  score
--      levels
--          level1 = 5
--          level2 = 4

ClearKey("score.levels")

--Afterwards, the registry will look like this:
--  score

</pre>
<hr/>
<a name='ListKeys'></a>
<h3 class='function'>
ListKeys
</h3>
<pre class='funcdef'><span class='retname'>children = </span>ListKeys(<span class='argname'>parent</span>)</pre>
<p>
Аргументы<br/> <span class="argname">parent</span> <span
class="argtype">(string)</span> – The parent registry key<br/>
<p>
Возвращаемое значение<br/> <span class="retname">children</span> <span
class="argtype">(table)</span> – Indexed table of strings with child
keys<br/>
<p>
List all child keys of a registry node.
<p>
</p>
<pre class='example'>
--If the registry looks like this:
--  score
--      levels
--          level1 = 5
--          level2 = 4

local list = ListKeys("score.levels")
for i=1, #list do
    print(list[i])
end

--This will output:
--level1
--level2

</pre>
<hr/>
<a name='HasKey'></a>
<h3 class='function'>
HasKey
</h3>
<pre class='funcdef'><span class='retname'>exists = </span>HasKey(<span class='argname'>key</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/>
<p>
Возвращаемое значение<br/> <span class="retname">exists</span> <span
class="argtype">(boolean)</span> – True if key exists<br/>
<p>
Returns true if the registry contains a certain key
<p>
</p>
<pre class='example'>
local foo = HasKey("score.levels")

</pre>
<hr/>
<a name='SetInt'></a>
<h3 class='function'>
SetInt
</h3>
<pre class='funcdef'><span class='retname'></span>SetInt(<span class='argname'>key, value</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/> <span
class="argname">value</span> <span class="argtype">(number)</span> –
Desired value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SetInt("score.levels.level1", 4)

</pre>
<hr/>
<a name='GetInt'></a>
<h3 class='function'>
GetInt
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetInt(<span class='argname'>key</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(number)</span> – Integer value of registry node or zero
if not found<br/>
<p><p>
</p>
<pre class='example'>
local a = GetInt("score.levels.level1")

</pre>
<hr/>
<a name='SetFloat'></a>
<h3 class='function'>
SetFloat
</h3>
<pre class='funcdef'><span class='retname'></span>SetFloat(<span class='argname'>key, value</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/> <span
class="argname">value</span> <span class="argtype">(number)</span> –
Desired value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SetFloat("level.time", 22.3)

</pre>
<hr/>
<a name='GetFloat'></a>
<h3 class='function'>
GetFloat
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetFloat(<span class='argname'>key</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(number)</span> – Float value of registry node or zero
if not found<br/>
<p><p>
</p>
<pre class='example'>
local time = GetFloat("level.time")

</pre>
<hr/>
<a name='SetBool'></a>
<h3 class='function'>
SetBool
</h3>
<pre class='funcdef'><span class='retname'></span>SetBool(<span class='argname'>key, value</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/> <span
class="argname">value</span> <span class="argtype">(boolean)</span> –
Desired value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SetBool("level.robots.enabled", true)

</pre>
<hr/>
<a name='GetBool'></a>
<h3 class='function'>
GetBool
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetBool(<span class='argname'>key</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(boolean)</span> – Boolean value of registry node or
false if not found<br/>
<p><p>
</p>
<pre class='example'>
local isRobotsEnabled = GetBool("level.robots.enabled")

</pre>
<hr/>
<a name='SetString'></a>
<h3 class='function'>
SetString
</h3>
<pre class='funcdef'><span class='retname'></span>SetString(<span class='argname'>key, value</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/> <span
class="argname">value</span> <span class="argtype">(string)</span> –
Desired value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SetBool("level.name", "foo")

</pre>
<hr/>
<a name='GetString'></a>
<h3 class='function'>
GetString
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetString(<span class='argname'>key</span>)</pre>
<p>
Аргументы<br/> <span class="argname">key</span> <span
class="argtype">(string)</span> – Registry key<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(string)</span> – String value of registry node or "" if
not found<br/>
<p><p>
</p>
<pre class='example'>
local name = GetString("level.name")

</pre>
<hr/>
<a name='Vec'></a>
<h3 class='function'>
Vec
</h3>
<pre class='funcdef'><span class='retname'>vec = </span>Vec(<span class='argname'>[x], [y], [z]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">x</span> <span
class="argtype">(number, optional)</span> – X value<br/> <span
class="argname">y</span> <span class="argtype">(number, optional)</span>
– Y value<br/> <span class="argname">z</span> <span
class="argtype">(number, optional)</span> – Z value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">vec</span> <span
class="argtype">(table)</span> – New vector<br/>
<p>
Create new vector and optionally initializes it to the provided values.
A Vec is equivalent to a regular lua table with three numbers.
<p>
</p>
<pre class='example'>
--These are equivalent
local a1 = Vec()
local a2 = {0, 0, 0}

--These are equivalent
local b1 = Vec(0, 1, 0)
local b2 = {0, 1, 0}

</pre>
<hr/>
<a name='VecCopy'></a>
<h3 class='function'>
VecCopy
</h3>
<pre class='funcdef'><span class='retname'>new = </span>VecCopy(<span class='argname'>org</span>)</pre>
<p>
Аргументы<br/> <span class="argname">org</span> <span
class="argtype">(table)</span> – A vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">new</span> <span
class="argtype">(table)</span> – Copy of org vector<br/>
<p>
Vectors should never be assigned like regular numbers. Since they are
implemented with lua tables assignment means two references pointing to
the same data. Use this function instead.
<p>
</p>
<pre class='example'>
--Do this to assign a vector
local right1 = Vec(1, 2, 3)
local right2 = VecCopy(right1)

--Never do this unless you REALLY know what you're doing
local wrong1 = Vec(1, 2, 3)
local wrong2 = wrong1

</pre>
<hr/>
<a name='VecLength'></a>
<h3 class='function'>
VecLength
</h3>
<pre class='funcdef'><span class='retname'>length = </span>VecLength(<span class='argname'>vec</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vec</span> <span
class="argtype">(table)</span> – A vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">length</span> <span
class="argtype">(number)</span> – Length (magnitude) of the vector<br/>
<p><p>
</p>
<pre class='example'>
local v = Vec(1,1,0)
local l = VecLength(v)

--l now equals 1.41421356

</pre>
<hr/>
<a name='VecNormalize'></a>
<h3 class='function'>
VecNormalize
</h3>
<pre class='funcdef'><span class='retname'>norm = </span>VecNormalize(<span class='argname'>vec</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vec</span> <span
class="argtype">(table)</span> – A vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">norm</span> <span
class="argtype">(table)</span> – A vector of length 1.0<br/>
<p>
If the input vector is of zero length, the function returns {0,0,1}
<p>
</p>
<pre class='example'>
local v = Vec(0,3,0)
local n = VecNormalize(v)

--n now equals {0,1,0}

</pre>
<hr/>
<a name='VecScale'></a>
<h3 class='function'>
VecScale
</h3>
<pre class='funcdef'><span class='retname'>norm = </span>VecScale(<span class='argname'>vec, scale</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vec</span> <span
class="argtype">(table)</span> – A vector<br/> <span
class="argname">scale</span> <span class="argtype">(number)</span> – A
scale factor<br/>
<p>
Возвращаемое значение<br/> <span class="retname">norm</span> <span
class="argtype">(table)</span> – A scaled version of input vector<br/>
<p><p>
</p>
<pre class='example'>
local v = Vec(1,2,3)
local n = VecScale(v, 2)

--n now equals {2,4,6}

</pre>
<hr/>
<a name='VecAdd'></a>
<h3 class='function'>
VecAdd
</h3>
<pre class='funcdef'><span class='retname'>c = </span>VecAdd(<span class='argname'>a, b</span>)</pre>
<p>
Аргументы<br/> <span class="argname">a</span> <span
class="argtype">(table)</span> – Vector<br/> <span
class="argname">b</span> <span class="argtype">(table)</span> –
Vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">c</span> <span
class="argtype">(table)</span> – New vector with sum of a and b<br/>
<p><p>
</p>
<pre class='example'>
local a = Vec(1,2,3)
local b = Vec(3,0,0)
local c = VecAdd(a, b)

--c now equals {4,2,3}

</pre>
<hr/>
<a name='VecSub'></a>
<h3 class='function'>
VecSub
</h3>
<pre class='funcdef'><span class='retname'>c = </span>VecSub(<span class='argname'>a, b</span>)</pre>
<p>
Аргументы<br/> <span class="argname">a</span> <span
class="argtype">(table)</span> – Vector<br/> <span
class="argname">b</span> <span class="argtype">(table)</span> –
Vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">c</span> <span
class="argtype">(table)</span> – New vector representing a-b<br/>
<p><p>
</p>
<pre class='example'>
local a = Vec(1,2,3)
local b = Vec(3,0,0)
local c = VecSub(a, b)

--c now equals {-2,2,3}

</pre>
<hr/>
<a name='VecDot'></a>
<h3 class='function'>
VecDot
</h3>
<pre class='funcdef'><span class='retname'>c = </span>VecDot(<span class='argname'>a, b</span>)</pre>
<p>
Аргументы<br/> <span class="argname">a</span> <span
class="argtype">(table)</span> – Vector<br/> <span
class="argname">b</span> <span class="argtype">(table)</span> –
Vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">c</span> <span
class="argtype">(number)</span> – Dot product of a and b<br/>
<p><p>
</p>
<pre class='example'>
local a = Vec(1,2,3)
local b = Vec(3,1,0)
local c = VecDot(a, b)

--c now equals 5

</pre>
<hr/>
<a name='VecCross'></a>
<h3 class='function'>
VecCross
</h3>
<pre class='funcdef'><span class='retname'>c = </span>VecCross(<span class='argname'>a, b</span>)</pre>
<p>
Аргументы<br/> <span class="argname">a</span> <span
class="argtype">(table)</span> – Vector<br/> <span
class="argname">b</span> <span class="argtype">(table)</span> –
Vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">c</span> <span
class="argtype">(table)</span> – Cross product of a and b (also called
vector product)<br/>
<p><p>
</p>
<pre class='example'>
local a = Vec(1,0,0)
local b = Vec(0,1,0)
local c = VecCross(a, b)

--c now equals {0,0,1}

</pre>
<hr/>
<a name='VecLerp'></a>
<h3 class='function'>
VecLerp
</h3>
<pre class='funcdef'><span class='retname'>c = </span>VecLerp(<span class='argname'>a, b, t</span>)</pre>
<p>
Аргументы<br/> <span class="argname">a</span> <span
class="argtype">(table)</span> – Vector<br/> <span
class="argname">b</span> <span class="argtype">(table)</span> –
Vector<br/> <span class="argname">t</span> <span
class="argtype">(number)</span> – fraction (usually between 0.0 and
1.0)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">c</span> <span
class="argtype">(table)</span> – Linearly interpolated vector between a
and b, using t<br/>
<p><p>
</p>
<pre class='example'>
local a = Vec(2,0,0)
local b = Vec(0,4,2)
local t = 0.5

--These two are equivalent
local c1 = VecLerp(a, b, t)
lcoal c2 = VecAdd(VecScale(a, 1-t), VecScale(b, t))

--c1 and c2 now equals {1, 2, 1}

</pre>
<hr/>
<a name='Quat'></a>
<h3 class='function'>
Quat
</h3>
<pre class='funcdef'><span class='retname'>quat = </span>Quat(<span class='argname'>[x], [y], [z], [w]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">x</span> <span
class="argtype">(number, optional)</span> – X value<br/> <span
class="argname">y</span> <span class="argtype">(number, optional)</span>
– Y value<br/> <span class="argname">z</span> <span
class="argtype">(number, optional)</span> – Z value<br/> <span
class="argname">w</span> <span class="argtype">(number, optional)</span>
– W value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">quat</span> <span
class="argtype">(table)</span> – New quaternion<br/>
<p>
Create new quaternion and optionally initializes it to the provided
values. Do not attempt to initialize a quaternion with raw values unless
you know what you are doing. Use QuatEuler or QuatAxisAngle instead. If
no аргументы are given, a unit quaternion will be created: {0, 0, 0, 1}.
A quaternion is equivalent to a regular lua table with four numbers.
<p>
</p>
<pre class='example'>
--These are equivalent
local a1 = Quat()
local a2 = {0, 0, 0, 1}

</pre>
<hr/>
<a name='QuatCopy'></a>
<h3 class='function'>
QuatCopy
</h3>
<pre class='funcdef'><span class='retname'>new = </span>QuatCopy(<span class='argname'>org</span>)</pre>
<p>
Аргументы<br/> <span class="argname">org</span> <span
class="argtype">(table)</span> – Quaternion<br/>
<p>
Возвращаемое значение<br/> <span class="retname">new</span> <span
class="argtype">(table)</span> – Copy of org quaternion<br/>
<p>
Quaternions should never be assigned like regular numbers. Since they
are implemented with lua tables assignment means two references pointing
to the same data. Use this function instead.
<p>
</p>
<pre class='example'>
--Do this to assign a quaternion
local right1 = QuatEuler(0, 90, 0)
local right2 = QuatCopy(right1)

--Never do this unless you REALLY know what you're doing
local wrong1 = QuatEuler(0, 90, 0)
local wrong2 = wrong1

</pre>
<hr/>
<a name='QuatAxisAngle'></a>
<h3 class='function'>
QuatAxisAngle
</h3>
<pre class='funcdef'><span class='retname'>quat = </span>QuatAxisAngle(<span class='argname'>axis, angle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">axis</span> <span
class="argtype">(table)</span> – Rotation axis, unit vector<br/> <span
class="argname">angle</span> <span class="argtype">(number)</span> –
Rotation angle in degrees<br/>
<p>
Возвращаемое значение<br/> <span class="retname">quat</span> <span
class="argtype">(table)</span> – New quaternion<br/>
<p>
Create a quaternion representing a rotation around a specific axis
<p>
</p>
<pre class='example'>
--Create quaternion representing rotation 30 degrees around Y axis
local q = QuatAxisAngle(Vec(0,1,0), 30)

</pre>
<hr/>
<a name='QuatEuler'></a>
<h3 class='function'>
QuatEuler
</h3>
<pre class='funcdef'><span class='retname'>quat = </span>QuatEuler(<span class='argname'>x, y, z</span>)</pre>
<p>
Аргументы<br/> <span class="argname">x</span> <span
class="argtype">(number)</span> – Angle around X axis in degrees,
sometimes also called roll or bank<br/> <span class="argname">y</span>
<span class="argtype">(number)</span> – Angle around Y axis in degrees,
sometimes also called yaw or heading<br/> <span class="argname">z</span>
<span class="argtype">(number)</span> – Angle around Z axis in degrees,
sometimes also called pitch or attitude<br/>
<p>
Возвращаемое значение<br/> <span class="retname">quat</span> <span
class="argtype">(table)</span> – New quaternion<br/>
<p>
Create quaternion using euler angle notation. The order of applied
rotations uses the "NASA standard aeroplane" model:
<ol>
<li>
Rotation around Y axis (yaw or heading)
</li>
<li>
Rotation around Z axis (pitch or attitude)
</li>
<li>
Rotation around X axis (roll or bank)
</li>
</ol>
<p>
</p>
<pre class='example'>
--Create quaternion representing rotation 30 degrees around Y axis and 25 degrees around Z axis
local q = QuatEuler(0, 30, 25)

</pre>
<hr/>
<a name='QuatLookAt'></a>
<h3 class='function'>
QuatLookAt
</h3>
<pre class='funcdef'><span class='retname'>quat = </span>QuatLookAt(<span class='argname'>eye, target</span>)</pre>
<p>
Аргументы<br/> <span class="argname">eye</span> <span
class="argtype">(table)</span> – Vector representing the camera
location<br/> <span class="argname">target</span> <span
class="argtype">(table)</span> – Vector representing the point to look
at<br/>
<p>
Возвращаемое значение<br/> <span class="retname">quat</span> <span
class="argtype">(table)</span> – New quaternion<br/>
<p>
Create a quaternion pointing the negative Z axis (forward) towards a
specific point, keeping the Y axis upwards. This is very useful for
creating camera transforms.
<p>
</p>
<pre class='example'>
local eye = Vec(0, 10, 0)
local target = Vec(0, 1, 5)
local rot = QuatLookAt(eye, target)
SetCameraTransform(Transform(eye, rot))

</pre>
<hr/>
<a name='QuatSlerp'></a>
<h3 class='function'>
QuatSlerp
</h3>
<pre class='funcdef'><span class='retname'>c = </span>QuatSlerp(<span class='argname'>a, b, t</span>)</pre>
<p>
Аргументы<br/> <span class="argname">a</span> <span
class="argtype">(table)</span> – Quaternion<br/> <span
class="argname">b</span> <span class="argtype">(table)</span> –
Quaternion<br/> <span class="argname">t</span> <span
class="argtype">(number)</span> – fraction (usually between 0.0 and
1.0)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">c</span> <span
class="argtype">(table)</span> – New quaternion<br/>
<p>
Spherical, linear interpolation between a and b, using t. This is very
useful for animating between two rotations.
<p>
</p>
<pre class='example'>
local a = QuatEuler(0, 10, 0)
local b = QuatEuler(0, 0, 45)

--Create quaternion half way between a and b
local q = QuatSlerp(a, b, 0.5)

</pre>
<hr/>
<a name='QuatRotateQuat'></a>
<h3 class='function'>
QuatRotateQuat
</h3>
<pre class='funcdef'><span class='retname'>c = </span>QuatRotateQuat(<span class='argname'>a, b</span>)</pre>
<p>
Аргументы<br/> <span class="argname">a</span> <span
class="argtype">(table)</span> – Quaternion<br/> <span
class="argname">b</span> <span class="argtype">(table)</span> –
Quaternion<br/>
<p>
Возвращаемое значение<br/> <span class="retname">c</span> <span
class="argtype">(table)</span> – New quaternion<br/>
<p>
Rotate one quaternion with another quaternion. This is mathematically
equivalent to c = a \* b using quaternion multiplication.
<p>
</p>
<pre class='example'>
local a = QuatEuler(0, 10, 0)
local b = QuatEuler(0, 0, 45)
local q = QuatRotateQuat(a, b)

--q now represents a rotation first 10 degrees around
--the Y axis and then 45 degrees around the Z axis.

</pre>
<hr/>
<a name='Transform'></a>
<h3 class='function'>
Transform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>Transform(<span class='argname'>[pos], [rot]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">pos</span> <span
class="argtype">(table, optional)</span> – Vector representing transform
position<br/> <span class="argname">rot</span> <span
class="argtype">(table, optional)</span> – Quaternion representing
transform rotation<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – New transform<br/>
<p>
A transform is a regular lua table with two entries: pos and rot, a
vector and quaternion representing transform position and rotation.
<p>
</p>
<pre class='example'>
--Create transform located at {0, 0, 0} with no rotation
local t1 = Transform()

--Create transform located at {10, 0, 0} with no rotation
local t2 = Transform(Vec(10, 0,0))

--Create transform located at {10, 0, 0}, rotated 45 degrees around Y axis
local t2 = Transform(Vec(10, 0,0), QuatEuler(0, 45, 0))

</pre>
<hr/>
<a name='TransformCopy'></a>
<h3 class='function'>
TransformCopy
</h3>
<pre class='funcdef'><span class='retname'>new = </span>TransformCopy(<span class='argname'>org</span>)</pre>
<p>
Аргументы<br/> <span class="argname">org</span> <span
class="argtype">(table)</span> – Transform<br/>
<p>
Возвращаемое значение<br/> <span class="retname">new</span> <span
class="argtype">(table)</span> – Copy of org transform<br/>
<p>
Transforms should never be assigned like regular numbers. Since they are
implemented with lua tables assignment means two references pointing to
the same data. Use this function instead.
<p>
</p>
<pre class='example'>
--Do this to assign a quaternion
local right1 = Transform(Vec(1,0,0), QuatEuler(0, 90, 0))
local right2 = TransformCopy(right1)

--Never do this unless you REALLY know what you're doing
local wrong1 = Transform(Vec(1,0,0), QuatEuler(0, 90, 0))
local wrong2 = wrong1

</pre>
<hr/>
<a name='TransformToParentTransform'></a>
<h3 class='function'>
TransformToParentTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>TransformToParentTransform(<span class='argname'>parent, child</span>)</pre>
<p>
Аргументы<br/> <span class="argname">parent</span> <span
class="argtype">(table)</span> – Transform<br/> <span
class="argname">child</span> <span class="argtype">(table)</span> –
Transform<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – New transform<br/>
<p>
Transform child transform out of the parent transform. This is the
opposite of TransformToLocalTransform.
<p>
</p>
<pre class='example'>
local b = GetBodyTransform(body)
local s = GetShapeLocalTransform(shape)

--b represents the location of body in world space
--s represents the location of shape in body space

local w = TransformToParentTransform(b, s)

--w now represents the location of shape in world space

</pre>
<hr/>
<a name='TransformToLocalTransform'></a>
<h3 class='function'>
TransformToLocalTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>TransformToLocalTransform(<span class='argname'>parent, child</span>)</pre>
<p>
Аргументы<br/> <span class="argname">parent</span> <span
class="argtype">(table)</span> – Transform<br/> <span
class="argname">child</span> <span class="argtype">(table)</span> –
Transform<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – New transform<br/>
<p>
Transform one transform into the local space of another transform. This
is the opposite of TransformToParentTransform.
<p>
</p>
<pre class='example'>
local b = GetBodyTransform(body)
local w = GetShapeWorldTransform(shape)

--b represents the location of body in world space
--w represents the location of shape in world space

local s = TransformToLocalTransform(b, w)

--s now represents the location of shape in body space.

</pre>
<hr/>
<a name='TransformToParentVec'></a>
<h3 class='function'>
TransformToParentVec
</h3>
<pre class='funcdef'><span class='retname'>r = </span>TransformToParentVec(<span class='argname'>t, v</span>)</pre>
<p>
Аргументы<br/> <span class="argname">t</span> <span
class="argtype">(table)</span> – Transform<br/> <span
class="argname">v</span> <span class="argtype">(table)</span> –
Vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">r</span> <span
class="argtype">(table)</span> – Transformed vector<br/>
<p>
Transfom vector v out of transform t only considering rotation.
<p>
</p>
<pre class='example'>
local t = GetBodyTransform(body)
local localUp = Vec(0, 1, 0)
local up = TransformToParentVec(t, localUp)

--up now represents the local body up direction in world space

</pre>
<hr/>
<a name='TransformToLocalVec'></a>
<h3 class='function'>
TransformToLocalVec
</h3>
<pre class='funcdef'><span class='retname'>r = </span>TransformToLocalVec(<span class='argname'>t, v</span>)</pre>
<p>
Аргументы<br/> <span class="argname">t</span> <span
class="argtype">(table)</span> – Transform<br/> <span
class="argname">v</span> <span class="argtype">(table)</span> –
Vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">r</span> <span
class="argtype">(table)</span> – Transformed vector<br/>
<p>
Transfom vector v into transform t only considering rotation.
<p>
</p>
<pre class='example'>
local t = GetBodyTransform(body)
local worldUp = Vec(0, 1, 0)
local up = TransformToLocalVec(t, worldUp)

--up now represents the world up direction in local body space

</pre>
<hr/>
<a name='TransformToParentPoint'></a>
<h3 class='function'>
TransformToParentPoint
</h3>
<pre class='funcdef'><span class='retname'>r = </span>TransformToParentPoint(<span class='argname'>t, p</span>)</pre>
<p>
Аргументы<br/> <span class="argname">t</span> <span
class="argtype">(table)</span> – Transform<br/> <span
class="argname">p</span> <span class="argtype">(table)</span> – Vector
representing position<br/>
<p>
Возвращаемое значение<br/> <span class="retname">r</span> <span
class="argtype">(table)</span> – Transformed position<br/>
<p>
Transfom position p out of transform t.
<p>
</p>
<pre class='example'>
local t = GetBodyTransform(body)
local bodyPoint = Vec(0, 0, -1)
local p = TransformToParentPoint(t, bodyPoint)

--p now represents the local body point {0, 0, -1 } in world space

</pre>
<hr/>
<a name='TransformToLocalPoint'></a>
<h3 class='function'>
TransformToLocalPoint
</h3>
<pre class='funcdef'><span class='retname'>r = </span>TransformToLocalPoint(<span class='argname'>t, p</span>)</pre>
<p>
Аргументы<br/> <span class="argname">t</span> <span
class="argtype">(table)</span> – Transform<br/> <span
class="argname">p</span> <span class="argtype">(table)</span> – Vector
representing position<br/>
<p>
Возвращаемое значение<br/> <span class="retname">r</span> <span
class="argtype">(table)</span> – Transformed position<br/>
<p>
Transfom position p into transform t.
<p>
</p>
<pre class='example'>
local t = GetBodyTransform(body)
local worldOrigo = Vec(0, 0, 0)
local p = TransformToLocalPoint(t, worldOrigo)

--p now represents the position of world origo in local body space

</pre>
<hr/>
<a name='SetTag'></a>
<h3 class='function'>
SetTag
</h3>
<pre class='funcdef'><span class='retname'></span>SetTag(<span class='argname'>handle, tag, [value]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/> <span
class="argname">tag</span> <span class="argtype">(string)</span> – Tag
name<br/> <span class="argname">value</span> <span
class="argtype">(string, optional)</span> – Tag value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
--Add "special" tag to an entity
SetTag(handle, "special")

--Add "team" tag to an entity and give it value "red"
SetTag(handle, "team", "red")

</pre>
<hr/>
<a name='RemoveTag'></a>
<h3 class='function'>
RemoveTag
</h3>
<pre class='funcdef'><span class='retname'></span>RemoveTag(<span class='argname'>handle, tag</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/> <span
class="argname">tag</span> <span class="argtype">(string)</span> – Tag
name<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Remove tag from an entity. If the tag had a value it is removed too.
<p>
</p>
<pre class='example'>
RemoveTag(handle, "special")

</pre>
<hr/>
<a name='HasTag'></a>
<h3 class='function'>
HasTag
</h3>
<pre class='funcdef'><span class='retname'>exists = </span>HasTag(<span class='argname'>handle, tag</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/> <span
class="argname">tag</span> <span class="argtype">(string)</span> – Tag
name<br/>
<p>
Возвращаемое значение<br/> <span class="retname">exists</span> <span
class="argtype">(boolean)</span> – Returns true if entity has tag<br/>
<p><p>
</p>
<pre class='example'>
SetTag(handle, "special")
local hasSpecial = HasTag(handle, "special") 
-- hasSpecial will be true

</pre>
<hr/>
<a name='GetTagValue'></a>
<h3 class='function'>
GetTagValue
</h3>
<pre class='funcdef'><span class='retname'>value = </span>GetTagValue(<span class='argname'>handle, tag</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/> <span
class="argname">tag</span> <span class="argtype">(string)</span> – Tag
name<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(string)</span> – Returns the tag value, if any. Empty
string otherwise.<br/>
<p><p>
</p>
<pre class='example'>

SetTag(handle, "special")
value = GetTagValue(handle, "special")
-- value will be ""

SetTag(handle, "special", "foo")
value = GetTagValue(handle, "special")
-- value will be "foo"

</pre>
<hr/>
<a name='GetDescription'></a>
<h3 class='function'>
GetDescription
</h3>
<pre class='funcdef'><span class='retname'>description = </span>GetDescription(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">description</span> <span
class="argtype">(string)</span> – The description string<br/>
<p>
All entities can have an associated description. For bodies and shapes
this can be provided through the editor. This function retrieves that
description.
<p>
</p>
<pre class='example'>
local desc = GetDescription(body)

</pre>
<hr/>
<a name='SetDescription'></a>
<h3 class='function'>
SetDescription
</h3>
<pre class='funcdef'><span class='retname'></span>SetDescription(<span class='argname'>handle, description</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/> <span
class="argname">description</span> <span class="argtype">(string)</span>
– The description string<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
All entities can have an associated description. The description for
bodies and shapes will show up on the HUD when looking at them.
<p>
</p>
<pre class='example'>
SetDescription(body, "Target object")

</pre>
<hr/>
<a name='Delete'></a>
<h3 class='function'>
Delete
</h3>
<pre class='funcdef'><span class='retname'></span>Delete(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Remove an entity from the scene. All entities owned by this entity will
also be removed.
<p>
</p>
<pre class='example'>
Delete(body)
--All shapes associated with body will also be removed

</pre>
<hr/>
<a name='IsHandleValid'></a>
<h3 class='function'>
IsHandleValid
</h3>
<pre class='funcdef'><span class='retname'>exists = </span>IsHandleValid(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Entity handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">exists</span> <span
class="argtype">(boolean)</span> – Returns true if the entity pointed to
by handle still exists<br/>
<p><p>
</p>
<pre class='example'>
valid = IsHandleValid(body)

--valid is true if body still exists

Delete(body)
valid = IsHandleValid(body)

--valid will now be false

</pre>
<hr/>
<a name='FindBody'></a>
<h3 class='function'>
FindBody
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindBody(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first body with specified
tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
--Search for a body tagged "target" in script scope
local target = FindBody("target")

--Search for a body tagged "escape" in entire scene
local escape = FindBody("escape", true)

</pre>
<hr/>
<a name='FindBodies'></a>
<h3 class='function'>
FindBodies
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindBodies(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
bodies with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Search for bodies tagged "target" in script scope
local targets = FindBodies("target")
for i=1, #targets do
    local target = targets[i]
    ...
end

</pre>
<hr/>
<a name='GetBodyTransform'></a>
<h3 class='function'>
GetBodyTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetBodyTransform(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Transform of the body<br/>
<p><p>
</p>
<pre class='example'>
local t = GetBodyTransform(body)

</pre>
<hr/>
<a name='SetBodyTransform'></a>
<h3 class='function'>
SetBodyTransform
</h3>
<pre class='funcdef'><span class='retname'></span>SetBodyTransform(<span class='argname'>handle, transform</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/> <span
class="argname">transform</span> <span class="argtype">(table)</span> –
Desired transform<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
--Move a body 1 meter upwards
local t = GetBodyTransform(body)
t.pos = VecAdd(t.pos, Vec(0, 1, 0))
SetBodyTransform(body, t)

</pre>
<hr/>
<a name='GetBodyMass'></a>
<h3 class='function'>
GetBodyMass
</h3>
<pre class='funcdef'><span class='retname'>mass = </span>GetBodyMass(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">mass</span> <span
class="argtype">(number)</span> – Body mass. Static bodies always return
zero mass.<br/>
<p><p>
</p>
<pre class='example'>
local mass = GetBodyMass(body)

</pre>
<hr/>
<a name='IsBodyDynamic'></a>
<h3 class='function'>
IsBodyDynamic
</h3>
<pre class='funcdef'><span class='retname'>dynamic = </span>IsBodyDynamic(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">dynamic</span> <span
class="argtype">(boolean)</span> – Return true if body is dynamic<br/>
<p>
Check if body is dynamic. Note that something that was created static
may become dynamic due to destruction.
<p>
</p>
<pre class='example'>
local dynamic = IsBodyDynamic(body)

</pre>
<hr/>
<a name='SetBodyDynamic'></a>
<h3 class='function'>
SetBodyDynamic
</h3>
<pre class='funcdef'><span class='retname'></span>SetBodyDynamic(<span class='argname'>handle, dynamic</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/> <span
class="argname">dynamic</span> <span class="argtype">(boolean)</span> –
True for dynamic. False for static.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Change the dynamic state of a body. There is very limited use for this
function. In most situations you should leave it up to the engine to
decide. Use with caution.
<p>
</p>
<pre class='example'>
SetBodyDynamic(body, false)

</pre>
<hr/>
<a name='SetBodyVelocity'></a>
<h3 class='function'>
SetBodyVelocity
</h3>
<pre class='funcdef'><span class='retname'></span>SetBodyVelocity(<span class='argname'>handle, velocity</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle (should be a dynamic
body)<br/> <span class="argname">velocity</span> <span
class="argtype">(table)</span> – Vector with linear velocity<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
This can be used for animating bodies with preserved physical
interaction, but in most cases you are better off with a motorized joint
instead.
<p>
</p>
<pre class='example'>
local vel = Vec(2,0,0)
SetBodyVelocity(body, vel)

</pre>
<hr/>
<a name='GetBodyVelocity'></a>
<h3 class='function'>
GetBodyVelocity
</h3>
<pre class='funcdef'><span class='retname'>velocity = </span>GetBodyVelocity(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle (should be a dynamic
body)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">velocity</span> <span
class="argtype">(table)</span> – Linear velocity as vector<br/>
<p><p>
</p>
<pre class='example'>
local linVel = GetBodyVelocity(body)

</pre>
<hr/>
<a name='GetBodyVelocityAtPos'></a>
<h3 class='function'>
GetBodyVelocityAtPos
</h3>
<pre class='funcdef'><span class='retname'>velocity = </span>GetBodyVelocityAtPos(<span class='argname'>handle, pos</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle (should be a dynamic
body)<br/> <span class="argname">pos</span> <span
class="argtype">(table)</span> – World space point as vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">velocity</span> <span
class="argtype">(table)</span> – Linear velocity on body at pos as
vector<br/>
<p>
Return the velocity on a body taking both linear and angular velocity
into account.
<p>
</p>
<pre class='example'>
local vel = GetBodyVelocityAtPos(body, pos)

</pre>
<hr/>
<a name='SetBodyAngularVelocity'></a>
<h3 class='function'>
SetBodyAngularVelocity
</h3>
<pre class='funcdef'><span class='retname'></span>SetBodyAngularVelocity(<span class='argname'>handle, angVel</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle (should be a dynamic
body)<br/> <span class="argname">angVel</span> <span
class="argtype">(table)</span> – Vector with angular velocity<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
This can be used for animating bodies with preserved physical
interaction, but in most cases you are better off with a motorized joint
instead.
<p>
</p>
<pre class='example'>
local angVel = Vec(2,0,0)
SetBodyAngularVelocity(body, angVel)

</pre>
<hr/>
<a name='GetBodyAngularVelocity'></a>
<h3 class='function'>
GetBodyAngularVelocity
</h3>
<pre class='funcdef'><span class='retname'>angVel = </span>GetBodyAngularVelocity(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle (should be a dynamic
body)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">angVel</span> <span
class="argtype">(table)</span> – Angular velocity as vector<br/>
<p><p>
</p>
<pre class='example'>
local angVel = GetBodyAngularVelocity(body)

</pre>
<hr/>
<a name='IsBodyActive'></a>
<h3 class='function'>
IsBodyActive
</h3>
<pre class='funcdef'><span class='retname'>active = </span>IsBodyActive(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">active</span> <span
class="argtype">(boolean)</span> – Return true if body is active<br/>
<p>
Check if body is body is currently simulated. For performance reasons,
bodies that don't move are taken out of the simulation. This function
can be used to query the active state of a specific body. Only dynamic
bodies can be active.
<p>
</p>
<pre class='example'>
if IsBodyActive(body) then
    ...
end

</pre>
<hr/>
<a name='ApplyBodyImpulse'></a>
<h3 class='function'>
ApplyBodyImpulse
</h3>
<pre class='funcdef'><span class='retname'></span>ApplyBodyImpulse(<span class='argname'>handle, position, velocity</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle (should be a dynamic
body)<br/> <span class="argname">position</span> <span
class="argtype">(table)</span> – World space position as vector<br/>
<span class="argname">velocity</span> <span
class="argtype">(table)</span> – World space impulse as vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Apply impulse to dynamic body at position (give body a push).
<p>
</p>
<pre class='example'>
local pos = Vec(0,1,0)
local imp = Vec(0,0,10)
ApplyBodyImpulse(body, pos, imp)

</pre>
<hr/>
<a name='GetBodyShapes'></a>
<h3 class='function'>
GetBodyShapes
</h3>
<pre class='funcdef'><span class='retname'>list = </span>GetBodyShapes(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table of shape handles<br/>
<p>
Return handles to all shapes owned by a body
<p>
</p>
<pre class='example'>
local shapes = GetBodyShapes(body)
for i=1,#shapes do
    local shape = shapes[i]
end

</pre>
<hr/>
<a name='GetBodyVehicle'></a>
<h3 class='function'>
GetBodyVehicle
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetBodyVehicle(<span class='argname'>body</span>)</pre>
<p>
Аргументы<br/> <span class="argname">body</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Get parent vehicle for body, or zero
if not part of vehicle<br/>
<p><p>
</p>
<pre class='example'>
local vehicle = GetBodyVehicle(body)

</pre>
<hr/>
<a name='GetBodyBounds'></a>
<h3 class='function'>
GetBodyBounds
</h3>
<pre class='funcdef'><span class='retname'>min, max = </span>GetBodyBounds(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">min</span> <span
class="argtype">(table)</span> – Vector representing the AABB lower
bound<br/> <span class="retname">max</span> <span
class="argtype">(table)</span> – Vector representing the AABB upper
bound<br/>
<p>
Return the world space, axis-aligned bounding box for a body.
<p>
</p>
<pre class='example'>
local min, max = GetBodyBounds(body)
local boundsSize = VecSub(max, min)
local center = VecLerp(min, max, 0.5)

</pre>
<hr/>
<a name='GetBodyCenterOfMass'></a>
<h3 class='function'>
GetBodyCenterOfMass
</h3>
<pre class='funcdef'><span class='retname'>point = </span>GetBodyCenterOfMass(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">point</span> <span
class="argtype">(table)</span> – Vector representing local center of
mass in body space<br/>
<p><p>
</p>
<pre class='example'>
--Visualize center of mass on for body
local com = GetBodyCenterOfMass(body)
local worldPoint = TransformToParentPoint(GetBodyTransform(body), com)
DebugCross(worldPoint)

</pre>
<hr/>
<a name='IsBodyVisible'></a>
<h3 class='function'>
IsBodyVisible
</h3>
<pre class='funcdef'><span class='retname'>visible = </span>IsBodyVisible(<span class='argname'>handle, maxDist, [rejectTransparent]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/> <span
class="argname">maxDist</span> <span class="argtype">(number)</span> –
Maximum visible distance<br/> <span
class="argname">rejectTransparent</span> <span class="argtype">(boolean,
optional)</span> – See through transparent materials. Default
false.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">visible</span> <span
class="argtype">(boolean)</span> – Return true if body is visible<br/>
<p>
This will check if a body is currently visible in the camera frustum and
not occluded by other objects.
<p>
</p>
<pre class='example'>
if IsBodyVisible(body, 25) then
    --Body is within 25 meters visible to the camera
end

</pre>
<hr/>
<a name='IsBodyBroken'></a>
<h3 class='function'>
IsBodyBroken
</h3>
<pre class='funcdef'><span class='retname'>broken = </span>IsBodyBroken(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">broken</span> <span
class="argtype">(boolean)</span> – Return true if body is broken<br/>
<p>
Determine if any shape of a body has been broken.
<p>
</p>
<pre class='example'>
local broken = IsBodyBroken(body)

</pre>
<hr/>
<a name='IsBodyJointedToStatic'></a>
<h3 class='function'>
IsBodyJointedToStatic
</h3>
<pre class='funcdef'><span class='retname'>result = </span>IsBodyJointedToStatic(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">result</span> <span
class="argtype">(boolean)</span> – Return true if body is in any way
connected to a static body<br/>
<p>
Determine if a body is in any way connected to a static object, either
by being static itself or be being directly or indirectly jointed to
something static.
<p>
</p>
<pre class='example'>
local connectedToStatic = IsBodyJointedToStatic(body)

</pre>
<hr/>
<a name='DrawBodyOutline'></a>
<h3 class='function'>
DrawBodyOutline
</h3>
<pre class='funcdef'><span class='retname'></span>DrawBodyOutline(<span class='argname'>handle, [r], [g], [b], a</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/> <span
class="argname">r</span> <span class="argtype">(number, optional)</span>
– Red<br/> <span class="argname">g</span> <span class="argtype">(number,
optional)</span> – Green<br/> <span class="argname">b</span> <span
class="argtype">(number, optional)</span> – Blue<br/> <span
class="argname">a</span> <span class="argtype">(number)</span> –
Alpha<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Render next frame with an outline around specified body. If no color is
given, a white outline will be drawn.
<p>
</p>
<pre class='example'>
--Draw white outline at 50% transparency
DrawBodyOutline(body, 0.5)

--Draw green outline, fully opaque
DrawBodyOutline(body, 0, 1, 0, 1)

</pre>
<hr/>
<a name='DrawBodyHighlight'></a>
<h3 class='function'>
DrawBodyHighlight
</h3>
<pre class='funcdef'><span class='retname'></span>DrawBodyHighlight(<span class='argname'>handle, amount</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/> <span
class="argname">amount</span> <span class="argtype">(number)</span> –
Amount<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Flash the appearance of a body when rendering this frame. This is used
for valuables in the game.
<p>
</p>
<pre class='example'>
DrawBodyHighlight(body, 0.5)

</pre>
<hr/>
<a name='FindShape'></a>
<h3 class='function'>
FindShape
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindShape(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first shape with specified
tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
--Search for a shape tagged "mybox" in script scope
local target = FindShape("mybox")

--Search for a shape tagged "laserturret" in entire scene
local escape = FindBody("laserturret", true)

</pre>
<hr/>
<a name='FindShapes'></a>
<h3 class='function'>
FindShapes
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindShapes(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
shapes with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Search for shapes tagged "alarmbox" in script scope
local shapes = FindShapes("alarmbox")
for i=1, #shapes do
    local shape = shapes[i]
    ...
end

</pre>
<hr/>
<a name='GetShapeLocalTransform'></a>
<h3 class='function'>
GetShapeLocalTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetShapeLocalTransform(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Return shape transform in body
space<br/>
<p><p>
</p>
<pre class='example'>
--Shape transform in body local space
local shapeTransform = GetShapeLocalTransform(shape)

--Body transform in world space
local bodyTransforn = GetBodyTransform(GetShapeBody(shape))

--Shape transform in world space
local worldTranform = TransformToParentTransform(bodyTransform, shapeTransform)

</pre>
<hr/>
<a name='SetShapeLocalTransform'></a>
<h3 class='function'>
SetShapeLocalTransform
</h3>
<pre class='funcdef'><span class='retname'></span>SetShapeLocalTransform(<span class='argname'>handle, transform</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/> <span
class="argname">transform</span> <span class="argtype">(table)</span> –
Shape transform in body space<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
local transform = Transform(Vec(0, 1, 0), QuatEuler(0, 90, 0))
SetShapeLocalTransform(shape, transform)

</pre>
<hr/>
<a name='GetShapeWorldTransform'></a>
<h3 class='function'>
GetShapeWorldTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetShapeWorldTransform(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Return shape transform in world
space<br/>
<p>
This is a convenience function, transforming the shape out of body space
<p>
</p>
<pre class='example'>
local worldTransform = GetShapeWorldTransform(shape)

--This is equivalent to
local shapeTransform = GetShapeLocalTransform(shape)
local bodyTransforn = GetBodyTransform(GetShapeBody(shape))
worldTranform = TransformToParentTransform(bodyTransform, shapeTransform)

</pre>
<hr/>
<a name='GetShapeBody'></a>
<h3 class='function'>
GetShapeBody
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetShapeBody(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Get handle to the body this shape is owned by. A shape is always owned
by a body, but can be transfered to a new body during destruction.
<p>
</p>
<pre class='example'>
local body = GetShapeBody(shape)

</pre>
<hr/>
<a name='GetShapeJoints'></a>
<h3 class='function'>
GetShapeJoints
</h3>
<pre class='funcdef'><span class='retname'>list = </span>GetShapeJoints(<span class='argname'>shape</span>)</pre>
<p>
Аргументы<br/> <span class="argname">shape</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with joints connected to
shape<br/>
<p><p>
</p>
<pre class='example'>
local hinges = GetShapeJoints(door)
for i=1, #hinges do
    local joint = hinges[i]
    ...
end

</pre>
<hr/>
<a name='GetShapeLights'></a>
<h3 class='function'>
GetShapeLights
</h3>
<pre class='funcdef'><span class='retname'>list = </span>GetShapeLights(<span class='argname'>shape</span>)</pre>
<p>
Аргументы<br/> <span class="argname">shape</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table of lights owned by
shape<br/>
<p><p>
</p>
<pre class='example'>
local lights = GetShapeLights(shape)
for i=1, #lights do
    local light = lights[i]
    ...
end

</pre>
<hr/>
<a name='GetShapeBounds'></a>
<h3 class='function'>
GetShapeBounds
</h3>
<pre class='funcdef'><span class='retname'>min, max = </span>GetShapeBounds(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">min</span> <span
class="argtype">(table)</span> – Vector representing the AABB lower
bound<br/> <span class="retname">max</span> <span
class="argtype">(table)</span> – Vector representing the AABB upper
bound<br/>
<p>
Return the world space, axis-aligned bounding box for a shape.
<p>
</p>
<pre class='example'>
local min, max = GetShapeBounds(shape)
local boundsSize = VecSub(max, min)
local center = VecLerp(min, max, 0.5)

</pre>
<hr/>
<a name='SetShapeEmissiveScale'></a>
<h3 class='function'>
SetShapeEmissiveScale
</h3>
<pre class='funcdef'><span class='retname'></span>SetShapeEmissiveScale(<span class='argname'>handle, scale</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/> <span
class="argname">scale</span> <span class="argtype">(number)</span> –
Scale factor for emissiveness<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Scale emissiveness for shape. If the shape has light sources attached,
their intensity will be scaled by the same amount.
<p>
</p>
<pre class='example'>
--Pulsate emissiveness and light intensity for shape
local scale = math.sin(GetTime())*0.5 + 0.5
SetShapeEmissiveScale(shape, scale)

</pre>
<hr/>
<a name='GetShapeMaterialAtPosition'></a>
<h3 class='function'>
GetShapeMaterialAtPosition
</h3>
<pre class='funcdef'><span class='retname'>type, r, g, b, a = </span>GetShapeMaterialAtPosition(<span class='argname'>handle, pos</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/> <span
class="argname">pos</span> <span class="argtype">(table)</span> –
Position in world space<br/>
<p>
Возвращаемое значение<br/> <span class="retname">type</span> <span
class="argtype">(string)</span> – Material type<br/> <span
class="retname">r</span> <span class="argtype">(number)</span> –
Red<br/> <span class="retname">g</span> <span
class="argtype">(number)</span> – Green<br/> <span
class="retname">b</span> <span class="argtype">(number)</span> –
Blue<br/> <span class="retname">a</span> <span
class="argtype">(number)</span> – Alpha<br/>
<p>
Return material properties for a particular voxel
<p>
</p>
<pre class='example'>
local hit, dist, normal, shape = QueryRaycast(pos, dir, 10)
if hit then
    local hitPoint = VecAdd(pos, VecScale(dir, dist))
    local mat = GetShapeMaterialAtPosition(shape, hitPoint)
    DebugPrint("Raycast hit voxel made out of " .. mat)
end

</pre>
<hr/>
<a name='GetShapeSize'></a>
<h3 class='function'>
GetShapeSize
</h3>
<pre class='funcdef'><span class='retname'>xsize, ysize, zsize = </span>GetShapeSize(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">xsize</span> <span
class="argtype">(number)</span> – Size in voxels along x axis<br/> <span
class="retname">ysize</span> <span class="argtype">(number)</span> –
Size in voxels along y axis<br/> <span class="retname">zsize</span>
<span class="argtype">(number)</span> – Size in voxels along z axis<br/>
<p>
Return the size of a shape in voxels
<p>
</p>
<pre class='example'>
local x, y, z = GetShapeSize(shape)

</pre>
<hr/>
<a name='GetShapeVoxelCount'></a>
<h3 class='function'>
GetShapeVoxelCount
</h3>
<pre class='funcdef'><span class='retname'>count = </span>GetShapeVoxelCount(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">count</span> <span
class="argtype">(number)</span> – Number of voxels in shape<br/>
<p>
Return the number of voxels in a shape, not including empty space
<p>
</p>
<pre class='example'>
local voxelCount = GetShapeVoxelCount(shape)

</pre>
<hr/>
<a name='IsShapeVisible'></a>
<h3 class='function'>
IsShapeVisible
</h3>
<pre class='funcdef'><span class='retname'>visible = </span>IsShapeVisible(<span class='argname'>handle, maxDist, [rejectTransparent]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/> <span
class="argname">maxDist</span> <span class="argtype">(number)</span> –
Maximum visible distance<br/> <span
class="argname">rejectTransparent</span> <span class="argtype">(boolean,
optional)</span> – See through transparent materials. Default
false.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">visible</span> <span
class="argtype">(boolean)</span> – Return true if shape is visible<br/>
<p>
This will check if a shape is currently visible in the camera frustum
and not occluded by other objects.
<p>
</p>
<pre class='example'>
if IsShapeVisible(shape, 25) then
    --Shape is within 25 meters visible to the camera
end

</pre>
<hr/>
<a name='IsShapeBroken'></a>
<h3 class='function'>
IsShapeBroken
</h3>
<pre class='funcdef'><span class='retname'>broken = </span>IsShapeBroken(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">broken</span> <span
class="argtype">(boolean)</span> – Return true if shape is broken<br/>
<p>
Determine if shape has been broken. Note that a shape can be transfered
to another body during destruction, but might still not be considered
broken if all voxels are intact.
<p>
</p>
<pre class='example'>
local broken = IsShapeBroken(shape)

</pre>
<hr/>
<a name='DrawShapeOutline'></a>
<h3 class='function'>
DrawShapeOutline
</h3>
<pre class='funcdef'><span class='retname'></span>DrawShapeOutline(<span class='argname'>handle, [r], [g], [b], a</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/> <span
class="argname">r</span> <span class="argtype">(number, optional)</span>
– Red<br/> <span class="argname">g</span> <span class="argtype">(number,
optional)</span> – Green<br/> <span class="argname">b</span> <span
class="argtype">(number, optional)</span> – Blue<br/> <span
class="argname">a</span> <span class="argtype">(number)</span> –
Alpha<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Render next frame with an outline around specified shape. If no color is
given, a white outline will be drawn.
<p>
</p>
<pre class='example'>
--Draw white outline at 50% transparency
DrawShapeOutline(shape, 0.5)

--Draw green outline, fully opaque
DrawShapeOutline(shape, 0, 1, 0, 1)

</pre>
<hr/>
<a name='DrawShapeHighlight'></a>
<h3 class='function'>
DrawShapeHighlight
</h3>
<pre class='funcdef'><span class='retname'></span>DrawShapeHighlight(<span class='argname'>handle, amount</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Shape handle<br/> <span
class="argname">amount</span> <span class="argtype">(number)</span> –
Amount<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Flash the appearance of a shape when rendering this frame.
<p>
</p>
<pre class='example'>
DrawShapeHighlight(shape, 0.5)

</pre>
<hr/>
<a name='FindLocation'></a>
<h3 class='function'>
FindLocation
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindLocation(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first location with
specified tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
local loc = FindLocation("start")

</pre>
<hr/>
<a name='FindLocations'></a>
<h3 class='function'>
FindLocations
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindLocations(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
locations with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Search for locations tagged "waypoint" in script scope
local locations = FindLocations("waypoint")
for i=1, #locs do
    local locs = locations[i]
    ...
end

</pre>
<hr/>
<a name='GetLocationTransform'></a>
<h3 class='function'>
GetLocationTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetLocationTransform(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Location handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Transform of the location<br/>
<p><p>
</p>
<pre class='example'>
local t = GetLocationTransform(loc)

</pre>
<hr/>
<a name='FindJoint'></a>
<h3 class='function'>
FindJoint
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindJoint(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first joint with specified
tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
local joint = FindLocation("doorhinge")

</pre>
<hr/>
<a name='FindJoints'></a>
<h3 class='function'>
FindJoints
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindJoints(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
joints with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Search for locations tagged "doorhinge" in script scope
local hinges = FindLocations("doorhinge")
for i=1, #hinges do
    local joint = hinges[i]
    ...
end

</pre>
<hr/>
<a name='IsJointBroken'></a>
<h3 class='function'>
IsJointBroken
</h3>
<pre class='funcdef'><span class='retname'>broken = </span>IsJointBroken(<span class='argname'>joint</span>)</pre>
<p>
Аргументы<br/> <span class="argname">joint</span> <span
class="argtype">(number)</span> – Joint handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">broken</span> <span
class="argtype">(boolean)</span> – True if joint is broken<br/>
<p><p>
</p>
<pre class='example'>
local broken = IsJointBroken(joint)

</pre>
<hr/>
<a name='GetJointType'></a>
<h3 class='function'>
GetJointType
</h3>
<pre class='funcdef'><span class='retname'>type = </span>GetJointType(<span class='argname'>joint</span>)</pre>
<p>
Аргументы<br/> <span class="argname">joint</span> <span
class="argtype">(number)</span> – Joint handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">type</span> <span
class="argtype">(string)</span> – Joint type<br/>
<p>
Joint type is one of the following: "ball", "hinge", "prismatic" or
"rope". An empty string is returned if joint handle is invalid.
<p>
</p>
<pre class='example'>
if GetJointType(joint) == "rope" then
    --Joint is rope
end

</pre>
<hr/>
<a name='GetJointOtherShape'></a>
<h3 class='function'>
GetJointOtherShape
</h3>
<pre class='funcdef'><span class='retname'>other = </span>GetJointOtherShape(<span class='argname'>joint, shape</span>)</pre>
<p>
Аргументы<br/> <span class="argname">joint</span> <span
class="argtype">(number)</span> – Joint handle<br/> <span
class="argname">shape</span> <span class="argtype">(number)</span> –
Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">other</span> <span
class="argtype">(number)</span> – Other shape handle<br/>
<p>
A joint is always connected to two shapes. Use this function if you know
one shape and want to find the other one.
<p>
</p>
<pre class='example'>
--joint is connected to a and b

otherShape = GetJointOtherShape(joint, a)
--otherShape is now b

otherShape = GetJointOtherShape(joint, b)
--otherShape is now a

</pre>
<hr/>
<a name='SetJointMotor'></a>
<h3 class='function'>
SetJointMotor
</h3>
<pre class='funcdef'><span class='retname'></span>SetJointMotor(<span class='argname'>joint, velocity, [strength]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">joint</span> <span
class="argtype">(number)</span> – Joint handle<br/> <span
class="argname">velocity</span> <span class="argtype">(number)</span> –
Desired velocity<br/> <span class="argname">strength</span> <span
class="argtype">(number, optional)</span> – Desired strength. Default is
infinite. Zero to disable.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Set joint motor target velocity. If joint is of type hinge, velocity is
given in radians per second angular velocity. If joint type is prismatic
joint velocity is given in meters per second. Calling this function will
override and void any previous call to SetJointMotorTarget.
<p>
</p>
<pre class='example'>
--Set motor speed to 0.5 radians per second
SetJointMotor(hinge, 0.5)

</pre>
<hr/>
<a name='SetJointMotorTarget'></a>
<h3 class='function'>
SetJointMotorTarget
</h3>
<pre class='funcdef'><span class='retname'></span>SetJointMotorTarget(<span class='argname'>joint, target, [maxVel], [strength]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">joint</span> <span
class="argtype">(number)</span> – Joint handle<br/> <span
class="argname">target</span> <span class="argtype">(number)</span> –
Desired movement target<br/> <span class="argname">maxVel</span> <span
class="argtype">(number, optional)</span> – Maximum velocity to reach
target. Default is infinite.<br/> <span class="argname">strength</span>
<span class="argtype">(number, optional)</span> – Desired strength.
Default is infinite. Zero to disable.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
If a joint has a motor target, it will try to maintain its relative
movement. This is very useful for elevators or other animated, jointed
mechanisms. If joint is of type hinge, target is an angle in degrees
(-180 to 180) and velocity is given in radians per second. If joint type
is prismatic, target is given in meters and velocity is given in meters
per second. Setting a motor target will override any previous call to
SetJointMotor.
<p>
</p>
<pre class='example'>
--Make joint reach a 45 degree angle, going at a maximum of 3 radians per second
SetJointMotorTarget(hinge, 45, 3)

</pre>
<hr/>
<a name='GetJointLimits'></a>
<h3 class='function'>
GetJointLimits
</h3>
<pre class='funcdef'><span class='retname'>min, max = </span>GetJointLimits(<span class='argname'>joint</span>)</pre>
<p>
Аргументы<br/> <span class="argname">joint</span> <span
class="argtype">(number)</span> – Joint handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">min</span> <span
class="argtype">(number)</span> – Minimum joint limit (angle or
distance)<br/> <span class="retname">max</span> <span
class="argtype">(number)</span> – Maximum joint limit (angle or
distance)<br/>
<p>
Return joint limits for hinge or prismatic joint. Returns angle or
distance depending on joint type.
<p>
</p>
<pre class='example'>
local min, max = GetJointLimits(hinge)

</pre>
<hr/>
<a name='GetJointMovement'></a>
<h3 class='function'>
GetJointMovement
</h3>
<pre class='funcdef'><span class='retname'>movement = </span>GetJointMovement(<span class='argname'>joint</span>)</pre>
<p>
Аргументы<br/> <span class="argname">joint</span> <span
class="argtype">(number)</span> – Joint handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">movement</span> <span
class="argtype">(number)</span> – Current joint position or angle<br/>
<p>
Return the current position or angle or the joint, measured in same way
as joint limits.
<p>
</p>
<pre class='example'>
local current = GetJointMovement(hinge)

</pre>
<hr/>
<a name='FindLight'></a>
<h3 class='function'>
FindLight
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindLight(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first light with specified
tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
local light = FindLight("main")

</pre>
<hr/>
<a name='FindLights'></a>
<h3 class='function'>
FindLights
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindLights(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
lights with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Search for lights tagged "main" in script scope
local lights = FindLights("main")
for i=1, #lights do
    local light = lights[i]
    ...
end

</pre>
<hr/>
<a name='SetLightEnabled'></a>
<h3 class='function'>
SetLightEnabled
</h3>
<pre class='funcdef'><span class='retname'></span>SetLightEnabled(<span class='argname'>handle, enabled</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Light handle<br/> <span
class="argname">enabled</span> <span class="argtype">(boolean)</span> –
Set to true if light should be enabled<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
If light is owned by a shape, the emissive scale of that shape will be
set to 0.0 when light is disabled and 1.0 when light is enabled.
<p>
</p>
<pre class='example'>
SetLightEnabled(light, false)

</pre>
<hr/>
<a name='SetLightColor'></a>
<h3 class='function'>
SetLightColor
</h3>
<pre class='funcdef'><span class='retname'></span>SetLightColor(<span class='argname'>handle, r, g, b</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Light handle<br/> <span
class="argname">r</span> <span class="argtype">(number)</span> – Red
value<br/> <span class="argname">g</span> <span
class="argtype">(number)</span> – Green value<br/> <span
class="argname">b</span> <span class="argtype">(number)</span> – Blue
value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
This will only set the color tint of the light. Use SetLightIntensity
for brightness. Setting the light color will not affect the emissive
color of a parent shape.
<p>
</p>
<pre class='example'>
--Set light color to yellow
SetLightColor(light, 1, 1, 0)

</pre>
<hr/>
<a name='SetLightIntensity'></a>
<h3 class='function'>
SetLightIntensity
</h3>
<pre class='funcdef'><span class='retname'></span>SetLightIntensity(<span class='argname'>handle, intensity</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Light handle<br/> <span
class="argname">intensity</span> <span class="argtype">(number)</span> –
Desired intensity of the light<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
If the shape is owned by a shape you most likely want to use
SetShapeEmissiveScale instead, which will affect both the emissiveness
of the shape and the brightness of the light at the same time.
<p>
</p>
<pre class='example'>
--Pulsate light
SetLightIntensity(light, math.sin(GetTime())*0.5 + 1.0)

</pre>
<hr/>
<a name='GetLightTransform'></a>
<h3 class='function'>
GetLightTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetLightTransform(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Light handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – World space light transform<br/>
<p>
Lights that are owned by a dynamic shape are automatcially moved with
that shape
<p>
</p>
<pre class='example'>
local pos = GetLightTransform(light).pos

</pre>
<hr/>
<a name='GetLightShape'></a>
<h3 class='function'>
GetLightShape
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetLightShape(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Light handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Shape handle or zero if not attached
to shape<br/>
<p><p>
</p>
<pre class='example'>
local shape = GetLightShape(light)

</pre>
<hr/>
<a name='IsPointAffectedByLight'></a>
<h3 class='function'>
IsPointAffectedByLight
</h3>
<pre class='funcdef'><span class='retname'>affected = </span>IsPointAffectedByLight(<span class='argname'>handle, point</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Light handle<br/> <span
class="argname">point</span> <span class="argtype">(table)</span> –
World space point as vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">affected</span> <span
class="argtype">(boolean)</span> – Return true if point is in light cone
and range<br/>
<p><p>
</p>
<pre class='example'>
local point = Vec(0, 10, 0)
local affected = IsPointAffectedByLight(light, point)

</pre>
<hr/>
<a name='FindTrigger'></a>
<h3 class='function'>
FindTrigger
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindTrigger(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first trigger with specified
tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
local goal = FindTrigger("goal")

</pre>
<hr/>
<a name='FindTriggers'></a>
<h3 class='function'>
FindTriggers
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindTriggers(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
triggers with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Find triggers tagged "toxic" in script scope
local triggers = FindTriggers("toxic")
for i=1, #triggers do
    local trigger = triggers[i]
    ...
end

</pre>
<hr/>
<a name='GetTriggerTransform'></a>
<h3 class='function'>
GetTriggerTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetTriggerTransform(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Trigger handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Current trigger transform in world
space<br/>
<p><p>
</p>
<pre class='example'>
local t = GetTriggerTransform(trigger)

</pre>
<hr/>
<a name='SetTriggerTransform'></a>
<h3 class='function'>
SetTriggerTransform
</h3>
<pre class='funcdef'><span class='retname'></span>SetTriggerTransform(<span class='argname'>handle, transform</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Trigger handle<br/> <span
class="argname">transform</span> <span class="argtype">(table)</span> –
Desired trigger transform in world space<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
local t = Transform(Vec(0, 1, 0), QuatEuler(0, 90, 0))
SetTriggerTransform(trigger, t)

</pre>
<hr/>
<a name='IsBodyInTrigger'></a>
<h3 class='function'>
IsBodyInTrigger
</h3>
<pre class='funcdef'><span class='retname'></span>IsBodyInTrigger(<span class='argname'>trigger, body</span>)</pre>
<p>
Аргументы<br/> <span class="argname">trigger</span> <span
class="argtype">(number)</span> – Trigger handle<br/> <span
class="argname">body</span> <span class="argtype">(number)</span> – Body
handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
This function will only check the center point of the body
<p>
</p>
<pre class='example'>
if IsBodyInTrigger(trigger, body) then
    ...
end

</pre>
<hr/>
<a name='IsVehicleInTrigger'></a>
<h3 class='function'>
IsVehicleInTrigger
</h3>
<pre class='funcdef'><span class='retname'></span>IsVehicleInTrigger(<span class='argname'>trigger, vehicle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">trigger</span> <span
class="argtype">(number)</span> – Trigger handle<br/> <span
class="argname">vehicle</span> <span class="argtype">(number)</span> –
Vehicle handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
This function will only check origo of vehicle
<p>
</p>
<pre class='example'>
if IsVehicleInTrigger(trigger, vehicle) then
    ...
end

</pre>
<hr/>
<a name='IsShapeInTrigger'></a>
<h3 class='function'>
IsShapeInTrigger
</h3>
<pre class='funcdef'><span class='retname'></span>IsShapeInTrigger(<span class='argname'>trigger, shape</span>)</pre>
<p>
Аргументы<br/> <span class="argname">trigger</span> <span
class="argtype">(number)</span> – Trigger handle<br/> <span
class="argname">shape</span> <span class="argtype">(number)</span> –
Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
This function will only check the center point of the shape
<p>
</p>
<pre class='example'>
if IsShapeInTrigger(trigger, shape) then
    ...
end

</pre>
<hr/>
<a name='IsPointInTrigger'></a>
<h3 class='function'>
IsPointInTrigger
</h3>
<pre class='funcdef'><span class='retname'></span>IsPointInTrigger(<span class='argname'>trigger, point</span>)</pre>
<p>
Аргументы<br/> <span class="argname">trigger</span> <span
class="argtype">(number)</span> – Trigger handle<br/> <span
class="argname">point</span> <span class="argtype">(table)</span> – Word
space point as vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
local p = Vec(0, 10, 0)
if IsPointInTrigger(trigger, p) then
    ...
end

</pre>
<hr/>
<a name='IsTriggerEmpty'></a>
<h3 class='function'>
IsTriggerEmpty
</h3>
<pre class='funcdef'><span class='retname'>empty, maxpoint = </span>IsTriggerEmpty(<span class='argname'>handle, [demolision]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Trigger handle<br/> <span
class="argname">demolision</span> <span class="argtype">(boolean,
optional)</span> – If true, small debris and vehicles are ignored<br/>
<p>
Возвращаемое значение<br/> <span class="retname">empty</span> <span
class="argtype">(boolean)</span> – True if trigger is empty<br/> <span
class="retname">maxpoint</span> <span class="argtype">(table)</span> –
World space point of highest point (largest Y coordinate) if not
empty<br/>
<p>
This function will check if trigger is empty. If trigger contains any
part of a body it will return false and the highest point as second
return value.
<p>
</p>
<pre class='example'>
local empty, highPoint = IsTriggerEmpty(trigger)
if not empty then
    --highPoint[2] is the tallest point in trigger
end

</pre>
<hr/>
<a name='FindScreen'></a>
<h3 class='function'>
FindScreen
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindScreen(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first screen with specified
tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
local screen = FindTrigger("tv")

</pre>
<hr/>
<a name='FindScreens'></a>
<h3 class='function'>
FindScreens
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindScreens(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
screens with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Find screens tagged "tv" in script scope
local screens = FindScreens("tv")
for i=1, #screens do
    local screen = screens[i]
    ...
end

</pre>
<hr/>
<a name='SetScreenEnabled'></a>
<h3 class='function'>
SetScreenEnabled
</h3>
<pre class='funcdef'><span class='retname'></span>SetScreenEnabled(<span class='argname'>screen, enabled</span>)</pre>
<p>
Аргументы<br/> <span class="argname">screen</span> <span
class="argtype">(number)</span> – Screen handle<br/> <span
class="argname">enabled</span> <span class="argtype">(boolean)</span> –
True if screen should be enabled<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Enable or disable screen
<p>
</p>
<pre class='example'>
SetScreenEnabled(screen, true)

</pre>
<hr/>
<a name='IsScreenEnabled'></a>
<h3 class='function'>
IsScreenEnabled
</h3>
<pre class='funcdef'><span class='retname'>enabled = </span>IsScreenEnabled(<span class='argname'>screen</span>)</pre>
<p>
Аргументы<br/> <span class="argname">screen</span> <span
class="argtype">(number)</span> – Screen handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">enabled</span> <span
class="argtype">(boolean)</span> – True if screen is enabled<br/>
<p><p>
</p>
<pre class='example'>
local b = IsScreenEnabled(screen)

</pre>
<hr/>
<a name='GetScreenShape'></a>
<h3 class='function'>
GetScreenShape
</h3>
<pre class='funcdef'><span class='retname'>shape = </span>GetScreenShape(<span class='argname'>screen</span>)</pre>
<p>
Аргументы<br/> <span class="argname">screen</span> <span
class="argtype">(number)</span> – Screen handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">shape</span> <span
class="argtype">(number)</span> – Shape handle or zero if none<br/>
<p>
Return handle to the parent shape of a screen
<p>
</p>
<pre class='example'>
local shape = GetScreenShape(screen)

</pre>
<hr/>
<a name='FindVehicle'></a>
<h3 class='function'>
FindVehicle
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>FindVehicle(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to first vehicle with specified
tag or zero if not found<br/>
<p><p>
</p>
<pre class='example'>
local vehicle = FindVehicle("mycar")

</pre>
<hr/>
<a name='FindVehicles'></a>
<h3 class='function'>
FindVehicles
</h3>
<pre class='funcdef'><span class='retname'>list = </span>FindVehicles(<span class='argname'>tag, [global]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">tag</span> <span
class="argtype">(string)</span> – Tag name<br/> <span
class="argname">global</span> <span class="argtype">(boolean,
optional)</span> – Search in entire scene<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
vehicles with specified tag<br/>
<p><p>
</p>
<pre class='example'>
--Find all vehicles in level tagged "boat"
local boats = FindVehicles("boat")
for i=1, #boats do
    local boat = boats[i]
    ...
end

</pre>
<hr/>
<a name='GetVehicleTransform'></a>
<h3 class='function'>
GetVehicleTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetVehicleTransform(<span class='argname'>vehicle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vehicle</span> <span
class="argtype">(number)</span> – Vehicle handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Transform of vehicle<br/>
<p><p>
</p>
<pre class='example'>
local t = GetVehicleTransform(vehicle)

</pre>
<hr/>
<a name='GetVehicleBody'></a>
<h3 class='function'>
GetVehicleBody
</h3>
<pre class='funcdef'><span class='retname'>body = </span>GetVehicleBody(<span class='argname'>vehicle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vehicle</span> <span
class="argtype">(number)</span> – Vehicle handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">body</span> <span
class="argtype">(number)</span> – Main body of vehicle<br/>
<p><p>
</p>
<pre class='example'>
local body = GetVehicleBody(vehicle)
if IsBodyBroken(body) then
--Vehicle body is broken
end

</pre>
<hr/>
<a name='GetVehicleHealth'></a>
<h3 class='function'>
GetVehicleHealth
</h3>
<pre class='funcdef'><span class='retname'>health = </span>GetVehicleHealth(<span class='argname'>vehicle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vehicle</span> <span
class="argtype">(number)</span> – Vehicle handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">health</span> <span
class="argtype">(number)</span> – Vehicle health (zero to one)<br/>
<p><p>
</p>
<pre class='example'>
local health = GetVehicleHealth(vehicle)

</pre>
<hr/>
<a name='GetVehicleDriverPos'></a>
<h3 class='function'>
GetVehicleDriverPos
</h3>
<pre class='funcdef'><span class='retname'>pos = </span>GetVehicleDriverPos(<span class='argname'>vehicle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vehicle</span> <span
class="argtype">(number)</span> – Vehicle handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">pos</span> <span
class="argtype">(table)</span> – Driver position as vector in vehicle
space<br/>
<p><p>
</p>
<pre class='example'>
local driverPos = GetVehicleDriverPos(vehicle)
local t = GetVehicleTransform(vehicle)
local worldPos = TransformToParentPoint(t, driverPos)

</pre>
<hr/>
<a name='DriveVehicle'></a>
<h3 class='function'>
DriveVehicle
</h3>
<pre class='funcdef'><span class='retname'></span>DriveVehicle(<span class='argname'>vehicle, drive, steering, handbrake</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vehicle</span> <span
class="argtype">(number)</span> – Vehicle handle<br/> <span
class="argname">drive</span> <span class="argtype">(number)</span> –
Reverse/forward control -1 to 1<br/> <span
class="argname">steering</span> <span class="argtype">(number)</span> –
Left/right control -1 to 1<br/> <span class="argname">handbrake</span>
<span class="argtype">(boolean)</span> – Handbrake control<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
This function applies input to vehicles, allowing for autonomous
driving. The vehicle will be turned on automatically and turned off when
no longer called. Call this from the tick function, not update.
<p>
</p>
<pre class='example'>
function tick()
    --Drive mycar forwards
    local v = FindVehicle("mycar")
    DriveVehicle(v, 1, 0, false)
end

</pre>
<hr/>
<a name='GetPlayerPos'></a>
<h3 class='function'>
GetPlayerPos
</h3>
<pre class='funcdef'><span class='retname'>position = </span>GetPlayerPos(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">position</span> <span
class="argtype">(table)</span> – Player center position<br/>
<p>
Return center point of player. This function is deprecated. Use
GetPlayerTransform instead.
<p>
</p>
<pre class='example'>
local p = GetPlayerPos()

--This is equivalent to
p = VecAdd(GetPlayerTransform().pos, Vec(0,1,0))

</pre>
<hr/>
<a name='GetPlayerTransform'></a>
<h3 class='function'>
GetPlayerTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetPlayerTransform(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Current player transform<br/>
<p>
The player transform is located at the bottom of the player. The player
transform considers heading (looking left and right). Forward is along
negative Z axis. Player pitch (looking up and down) does not affect
player transform. If you want the transform of the eye, use
GetPlayerCameraTransform() instead.
<p>
</p>
<pre class='example'>
local t = GetPlayerTransform()

</pre>
<hr/>
<a name='SetPlayerTransform'></a>
<h3 class='function'>
SetPlayerTransform
</h3>
<pre class='funcdef'><span class='retname'></span>SetPlayerTransform(<span class='argname'>transform</span>)</pre>
<p>
Аргументы<br/> <span class="argname">transform</span> <span
class="argtype">(table)</span> – Desired player transform<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Instantly teleport the player to desired transform. Player velocity and
up/down look angle will be set to zero during this process.
<p>
</p>
<pre class='example'>
local t = Transform(Vec(10, 0, 0), QuatEuler(0, 90, 0))
SetPlayerTransform(t)

</pre>
<hr/>
<a name='GetPlayerCameraTransform'></a>
<h3 class='function'>
GetPlayerCameraTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetPlayerCameraTransform(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Current player camera transform<br/>
<p>
The player camera transform is usually the same as what you get from
GetCameraTransform, but if you have set a camera transform manually with
SetCameraTransform, you can retrieve the standard player camera
transform with this function.
<p>
</p>
<pre class='example'>
local t = GetPlayerCameraTransform()

</pre>
<hr/>
<a name='SetPlayerSpawnTransform'></a>
<h3 class='function'>
SetPlayerSpawnTransform
</h3>
<pre class='funcdef'><span class='retname'></span>SetPlayerSpawnTransform(<span class='argname'>transform</span>)</pre>
<p>
Аргументы<br/> <span class="argname">transform</span> <span
class="argtype">(table)</span> – Desired player spawn transform<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Call this function during init to alter the player spawn transform.
<p>
</p>
<pre class='example'>
local t = Transform(Vec(10, 0, 0), QuatEuler(0, 90, 0))
SetPlayerSpawnTransform(t)

</pre>
<hr/>
<a name='GetPlayerVelocity'></a>
<h3 class='function'>
GetPlayerVelocity
</h3>
<pre class='funcdef'><span class='retname'>velocity = </span>GetPlayerVelocity(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">velocity</span> <span
class="argtype">(table)</span> – Player velocity in world space as
vector<br/>
<p><p>
</p>
<pre class='example'>
local vel = GetPlayerVelocity()

</pre>
<hr/>
<a name='SetPlayerVehicle'></a>
<h3 class='function'>
SetPlayerVehicle
</h3>
<pre class='funcdef'><span class='retname'></span>SetPlayerVehicle(<span class='argname'>vehicle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vehicle</span> <span
class="argtype">(value)</span> – Handle to vehicle or zero to not
drive.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Drive specified vehicle.
<p>
</p>
<pre class='example'>
local car = FindVehicle("mycar")
SetPlayerVehicle(car)

</pre>
<hr/>
<a name='SetPlayerVelocity'></a>
<h3 class='function'>
SetPlayerVelocity
</h3>
<pre class='funcdef'><span class='retname'></span>SetPlayerVelocity(<span class='argname'>velocity</span>)</pre>
<p>
Аргументы<br/> <span class="argname">velocity</span> <span
class="argtype">(table)</span> – Player velocity in world space as
vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SetPlayerVelocity(Vec(0, 5, 0))

</pre>
<hr/>
<a name='GetPlayerVehicle'></a>
<h3 class='function'>
GetPlayerVehicle
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerVehicle(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Current vehicle handle, or zero if not
in vehicle<br/>
<p><p>
</p>
<pre class='example'>
local vehicle = GetPlayerVehicle()
if vehicle ~= 0 then
    ...
end

</pre>
<hr/>
<a name='GetPlayerGrabShape'></a>
<h3 class='function'>
GetPlayerGrabShape
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerGrabShape(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to grabbed shape or zero if not
grabbing.<br/>
<p><p>
</p>
<pre class='example'>
local shape = GetPlayerGrabShape()
if shape ~= 0 then
    ...
end

</pre>
<hr/>
<a name='GetPlayerGrabBody'></a>
<h3 class='function'>
GetPlayerGrabBody
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerGrabBody(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to grabbed body or zero if not
grabbing.<br/>
<p><p>
</p>
<pre class='example'>
local body = GetPlayerGrabBody()
if body ~= 0 then
    ...
end

</pre>
<hr/>
<a name='GetPlayerPickShape'></a>
<h3 class='function'>
GetPlayerPickShape
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerPickShape(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to picked shape or zero if
nothing is picked<br/>
<p><p>
</p>
<pre class='example'>
local shape = GetPlayerPickShape()
if shape ~= 0 then
    ...
end

</pre>
<hr/>
<a name='GetPlayerPickBody'></a>
<h3 class='function'>
GetPlayerPickBody
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerPickBody(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to picked body or zero if
nothing is picked<br/>
<p><p>
</p>
<pre class='example'>
local body = GetPlayerPickBody()
if body ~= 0 then
    ...
end

</pre>
<hr/>
<a name='GetPlayerInteractShape'></a>
<h3 class='function'>
GetPlayerInteractShape
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerInteractShape(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to interactable shape or
zero<br/>
<p>
Interactable shapes has to be tagged with "interact". The engine
determines which interactable shape is currently interactable.
<p>
</p>
<pre class='example'>
local shape = GetPlayerInteractShape()
if shape ~= 0 then
    ...
end

</pre>
<hr/>
<a name='GetPlayerInteractBody'></a>
<h3 class='function'>
GetPlayerInteractBody
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerInteractBody(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to interactable body or
zero<br/>
<p>
Interactable shapes has to be tagged with "interact". The engine
determines which interactable body is currently interactable.
<p>
</p>
<pre class='example'>
local body = GetPlayerInteractBody()
if body ~= 0 then
    ...
end

</pre>
<hr/>
<a name='SetPlayerScreen'></a>
<h3 class='function'>
SetPlayerScreen
</h3>
<pre class='funcdef'><span class='retname'></span>SetPlayerScreen(<span class='argname'>handle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Handle to screen or zero for no
screen<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Set the screen the player should interact with. For the screen to
feature a mouse pointer and receieve input, the screen also needs to
have interactive property.
<p>
</p>
<pre class='example'>
--Interact with screen
SetPlayerScreen(screen)

--Do not interact with screen
SetPlayerScreen(0)

</pre>
<hr/>
<a name='GetPlayerScreen'></a>
<h3 class='function'>
GetPlayerScreen
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetPlayerScreen(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to interacted screen or zero if
none<br/>
<p><p>
</p>
<pre class='example'>
--Interact with screen
local screen = GetPlayerScreen()

</pre>
<hr/>
<a name='SetPlayerHealth'></a>
<h3 class='function'>
SetPlayerHealth
</h3>
<pre class='funcdef'><span class='retname'></span>SetPlayerHealth(<span class='argname'>health</span>)</pre>
<p>
Аргументы<br/> <span class="argname">health</span> <span
class="argtype">(number)</span> – Set player health (between zero and
one)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SetPlayerHealth(0.5)

</pre>
<hr/>
<a name='GetPlayerHealth'></a>
<h3 class='function'>
GetPlayerHealth
</h3>
<pre class='funcdef'><span class='retname'>health = </span>GetPlayerHealth(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">health</span> <span
class="argtype">(number)</span> – Current player health<br/>
<p><p>
</p>
<pre class='example'>
local health = GetPlayerHealth()

</pre>
<hr/>
<a name='RespawnPlayer'></a>
<h3 class='function'>
RespawnPlayer
</h3>
<pre class='funcdef'><span class='retname'></span>RespawnPlayer(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Respawn player at spawn position without modifying the scene
<p>
</p>
<pre class='example'>
RespawnPlayer()

</pre>
<hr/>
<a name='RegisterTool'></a>
<h3 class='function'>
RegisterTool
</h3>
<pre class='funcdef'><span class='retname'></span>RegisterTool(<span class='argname'>id, name, file</span>)</pre>
<p>
Аргументы<br/> <span class="argname">id</span> <span
class="argtype">(string)</span> – Tool unique identifier<br/> <span
class="argname">name</span> <span class="argtype">(string)</span> – Tool
name to show in hud<br/> <span class="argname">file</span> <span
class="argtype">(string)</span> – Path to vox file<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Register a custom tool that will show up in the player inventory and can
be selected with scroll wheel. Do this only once per tool. You also need
to enable the tool in the registry before it can be used.
<p>
</p>
<pre class='example'>
function init()
    RegisterTool("lasergun", "Laser Gun", "MOD/vox/lasergun.vox")
    SetBool("game.tool.lasergun.enabled", true)
end

function tick()
    if GetString("game.player.tool") == "lasergun" then
        --Tool is selected. Tool logic goes here.
    end
end

</pre>
<hr/>
<a name='GetToolBody'></a>
<h3 class='function'>
GetToolBody
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>GetToolBody(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to currently visible tool body
or zero if none<br/>
<p>
Return body handle of the visible tool. You can use this to retrieve
tool shapes and animate them, change emissiveness, etc. Do not attempt
to set the tool body transform, since it is controlled by the engine.
Use SetToolTranform for that.
<p>
</p>
<pre class='example'>
local toolBody = GetToolBody()
if toolBody~=0 then
    ...
end

</pre>
<hr/>
<a name='SetToolTransform'></a>
<h3 class='function'>
SetToolTransform
</h3>
<pre class='funcdef'><span class='retname'></span>SetToolTransform(<span class='argname'>transform</span>)</pre>
<p>
Аргументы<br/> <span class="argname">transform</span> <span
class="argtype">(table)</span> – Tool body transform<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Apply an additional transform on the visible tool body. This can be used
to create tool animations. You need to set this every frame from the
tick function.
<p>
</p>
<pre class='example'>
--Offset the tool half a meter to the right
local offset = Transform(Vec(0.5, 0, 0))
SetToolTransform(offset)

</pre>
<hr/>
<a name='LoadSound'></a>
<h3 class='function'>
LoadSound
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>LoadSound(<span class='argname'>path</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to ogg sound file<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Sound handle<br/>
<p><p>
</p>
<pre class='example'>
local snd = LoadSound("beep.ogg")

</pre>
<hr/>
<a name='LoadLoop'></a>
<h3 class='function'>
LoadLoop
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>LoadLoop(<span class='argname'>path</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to ogg sound file<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Loop handle<br/>
<p><p>
</p>
<pre class='example'>
local loop = LoadLoop("siren.ogg")

</pre>
<hr/>
<a name='PlaySound'></a>
<h3 class='function'>
PlaySound
</h3>
<pre class='funcdef'><span class='retname'></span>PlaySound(<span class='argname'>handle, [pos], [volume]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Sound handle<br/> <span
class="argname">pos</span> <span class="argtype">(table,
optional)</span> – World position as vector. Default is player
position.<br/> <span class="argname">volume</span> <span
class="argtype">(number, optional)</span> – Playback volume. Default is
1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
function init()
    snd = LoadSound("beep.ogg")
end

function tick()
    if trigSound then
        local pos = Vec(100, 0, 0)
        PlaySound(snd, pos, 0.5)
    end
end

</pre>
<hr/>
<a name='PlayLoop'></a>
<h3 class='function'>
PlayLoop
</h3>
<pre class='funcdef'><span class='retname'></span>PlayLoop(<span class='argname'>handle, [pos], [volume]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Loop handle<br/> <span
class="argname">pos</span> <span class="argtype">(table,
optional)</span> – World position as vector. Default is player
position.<br/> <span class="argname">volume</span> <span
class="argtype">(number, optional)</span> – Playback volume. Default is
1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Call this function continuously to play loop
<p>
</p>
<pre class='example'>
function init()
    loop = LoadLoop("siren.ogg")
end

function tick()
    local pos = Vec(100, 0, 0)
    PlayLoop(loop, pos, 0.5)
end

</pre>
<hr/>
<a name='PlayMusic'></a>
<h3 class='function'>
PlayMusic
</h3>
<pre class='funcdef'><span class='retname'></span>PlayMusic(<span class='argname'>path</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Music path<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
PlayMusic("MOD/music/background.ogg")

</pre>
<hr/>
<a name='StopMusic'></a>
<h3 class='function'>
StopMusic
</h3>
<pre class='funcdef'><span class='retname'></span>StopMusic(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
StopMusic()

</pre>
<hr/>
<a name='LoadSprite'></a>
<h3 class='function'>
LoadSprite
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>LoadSprite(<span class='argname'>path</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to sprite. Must be PNG or JPG
format.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Sprite handle<br/>
<p><p>
</p>
<pre class='example'>
function init()
    arrow = LoadSprite("arrow.png")
end

</pre>
<hr/>
<a name='DrawSprite'></a>
<h3 class='function'>
DrawSprite
</h3>
<pre class='funcdef'><span class='retname'></span>DrawSprite(<span class='argname'>handle, transform, width, height, r, g, b, a, [depthTest], [additive]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">handle</span> <span
class="argtype">(number)</span> – Sprite handle<br/> <span
class="argname">transform</span> <span class="argtype">(table)</span> –
Transform<br/> <span class="argname">width</span> <span
class="argtype">(number)</span> – Width in meters<br/> <span
class="argname">height</span> <span class="argtype">(number)</span> –
Height in meters<br/> <span class="argname">r</span> <span
class="argtype">(number)</span> – Red color<br/> <span
class="argname">g</span> <span class="argtype">(number)</span> – Green
color<br/> <span class="argname">b</span> <span
class="argtype">(number)</span> – Blue color<br/> <span
class="argname">a</span> <span class="argtype">(number)</span> –
Alpha<br/> <span class="argname">depthTest</span> <span
class="argtype">(boolean, optional)</span> – Depth test enabled. Default
false.<br/> <span class="argname">additive</span> <span
class="argtype">(boolean, optional)</span> – Additive blending enabled.
Default false.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Draw sprite in world at next frame. Call this function from the tick
callback.
<p>
</p>
<pre class='example'>
function init()
    arrow = LoadSprite("arrow.png")
end

function tick()
    --Draw sprite using transform
    --Size is two meters in width and height
    --Color is white, fully opaue
    local t = Transform(Vec(0, 10, 0), QuatEuler(0, GetTime(), 0))
    DrawSprite(arrow, t, 2, 2, 1, 1, 1, 1)
end

</pre>
<hr/>
<a name='QueryRequire'></a>
<h3 class='function'>
QueryRequire
</h3>
<pre class='funcdef'><span class='retname'></span>QueryRequire(<span class='argname'>layers</span>)</pre>
<p>
Аргументы<br/> <span class="argname">layers</span> <span
class="argtype">(string)</span> – Space separate list of layers<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Set required layers for next query. Available layers are:
<table border=0><tr><td class='header'>
 Layer 
</td><td class='header'>
 Описание
</td></tr>
<tr><td class='first' valign='top'>
physical
</td><td valign='top'> 
have a physical representation
</td></tr><tr><td class='first' valign='top'>
dynamic
</td><td valign='top'> 
part of a dynamic body
</td></tr><tr><td class='first' valign='top'>
static
</td><td valign='top'> 
part of a static body
</td></tr><tr><td class='first' valign='top'>
large
</td><td valign='top'> 
above debris threshold
</td></tr><tr><td class='first' valign='top'>
small
</td><td valign='top'> 
below debris threshold
</td></tr><table/>
<p>
</p>
<pre class='example'>
--Raycast dynamic, physical objects above debris threshold, but not specific vehicle
QueryRequire("physical dynamic large")
QueryRejectVehicle(vehicle)
QueryRaycast(...)

</pre>
<hr/>
<a name='QueryRejectVehicle'></a>
<h3 class='function'>
QueryRejectVehicle
</h3>
<pre class='funcdef'><span class='retname'></span>QueryRejectVehicle(<span class='argname'>vehicle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">vehicle</span> <span
class="argtype">(number)</span> – Vehicle handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Exclude vehicle from the next query
<p>
</p>
<pre class='example'>
--Do not include vehicle in next raycast
QueryRejectVehicle(vehicle)
QueryRaycast(...)

</pre>
<hr/>
<a name='QueryRejectBody'></a>
<h3 class='function'>
QueryRejectBody
</h3>
<pre class='funcdef'><span class='retname'></span>QueryRejectBody(<span class='argname'>body</span>)</pre>
<p>
Аргументы<br/> <span class="argname">body</span> <span
class="argtype">(number)</span> – Body handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Exclude body from the next query
<p>
</p>
<pre class='example'>
--Do not include body in next raycast
QueryRejectBody(body)
QueryRaycast(...)

</pre>
<hr/>
<a name='QueryRejectShape'></a>
<h3 class='function'>
QueryRejectShape
</h3>
<pre class='funcdef'><span class='retname'></span>QueryRejectShape(<span class='argname'>shape</span>)</pre>
<p>
Аргументы<br/> <span class="argname">shape</span> <span
class="argtype">(number)</span> – Shape handle<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Exclude shape from the next query
<p>
</p>
<pre class='example'>
--Do not include shape in next raycast
QueryRejectShape(shape)
QueryRaycast(...)

</pre>
<hr/>
<a name='QueryRaycast'></a>
<h3 class='function'>
QueryRaycast
</h3>
<pre class='funcdef'><span class='retname'>hit, dist, normal, shape = </span>QueryRaycast(<span class='argname'>origin, direction, maxDist, [radius], [rejectTransparent]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">origin</span> <span
class="argtype">(table)</span> – Raycast origin as world space
vector<br/> <span class="argname">direction</span> <span
class="argtype">(table)</span> – Unit length raycast direction as world
space vector<br/> <span class="argname">maxDist</span> <span
class="argtype">(number)</span> – Raycast maximum distance. Keep this as
low as possible for good performance.<br/> <span
class="argname">radius</span> <span class="argtype">(number,
optional)</span> – Raycast thickness. Default zero.<br/> <span
class="argname">rejectTransparent</span> <span class="argtype">(boolean,
optional)</span> – Raycast through transparent materials. Default
false.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">hit</span> <span
class="argtype">(boolean)</span> – True if raycast hit something<br/>
<span class="retname">dist</span> <span class="argtype">(number)</span>
– Hit distance from origin<br/> <span class="retname">normal</span>
<span class="argtype">(table)</span> – World space normal at hit
point<br/> <span class="retname">shape</span> <span
class="argtype">(number)</span> – Handle to hit shape<br/>
<p>
This will perform a raycast or spherecast (if radius is more than zero)
query. If you want to set up a filter for the query you need to do so
before every call to this function.
<p>
</p>
<pre class='example'>
--Raycast from a high point straight downwards, excluding a specific vehicle
QueryRejectVehicle(vehicle)
local hit, d = QueryRaycast(Vec(0, 100, 0), Vec(0, -1, 0), 100)
if hit then
    ...hit something at distance d
end

</pre>
<hr/>
<a name='QueryClosestPoint'></a>
<h3 class='function'>
QueryClosestPoint
</h3>
<pre class='funcdef'><span class='retname'>hit, point, normal, shape = </span>QueryClosestPoint(<span class='argname'>origin, maxDist</span>)</pre>
<p>
Аргументы<br/> <span class="argname">origin</span> <span
class="argtype">(table)</span> – World space point<br/> <span
class="argname">maxDist</span> <span class="argtype">(number)</span> –
Maximum distance. Keep this as low as possible for good
performance.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">hit</span> <span
class="argtype">(boolean)</span> – True if a point was found<br/> <span
class="retname">point</span> <span class="argtype">(table)</span> –
World space closest point<br/> <span class="retname">normal</span> <span
class="argtype">(table)</span> – World space normal at closest
point<br/> <span class="retname">shape</span> <span
class="argtype">(number)</span> – Handle to closest shape<br/>
<p>
This will query the closest point to all shapes in the world. If you
want to set up a filter for the query you need to do so before every
call to this function.
<p>
</p>
<pre class='example'>
--Find closest point within 10 meters of {0, 5, 0}, excluding any point on myVehicle
QueryRejectVehicle(myVehicle)
local hit, p, n, s = QueryClosestPoint(Vec(0, 5, 0), 10)
if hit then
    --Point p of shape s is closest
end

</pre>
<hr/>
<a name='QueryAabbShapes'></a>
<h3 class='function'>
QueryAabbShapes
</h3>
<pre class='funcdef'><span class='retname'>list = </span>QueryAabbShapes(<span class='argname'>min, max</span>)</pre>
<p>
Аргументы<br/> <span class="argname">min</span> <span
class="argtype">(table)</span> – Aabb minimum point<br/> <span
class="argname">max</span> <span class="argtype">(table)</span> – Aabb
maximum point<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
shapes in the aabb<br/>
<p>
Return all shapes within the provided world space, axis-aligned bounding
box
<p>
</p>
<pre class='example'>
local list = QueryAabbShapes(Vec(0, 0, 0), Vec(10, 10, 10))
for i=1, #list do
    local shape = list[i]
    ..
end

</pre>
<hr/>
<a name='QueryAabbBodies'></a>
<h3 class='function'>
QueryAabbBodies
</h3>
<pre class='funcdef'><span class='retname'>list = </span>QueryAabbBodies(<span class='argname'>min, max</span>)</pre>
<p>
Аргументы<br/> <span class="argname">min</span> <span
class="argtype">(table)</span> – Aabb minimum point<br/> <span
class="argname">max</span> <span class="argtype">(table)</span> – Aabb
maximum point<br/>
<p>
Возвращаемое значение<br/> <span class="retname">list</span> <span
class="argtype">(table)</span> – Indexed table with handles to all
bodies in the aabb<br/>
<p>
Return all bodies within the provided world space, axis-aligned bounding
box
<p>
</p>
<pre class='example'>
local list = QueryAabbBodies(Vec(0, 0, 0), Vec(10, 10, 10))
for i=1, #list do
    local body = list[i]
    ..
end

</pre>
<hr/>
<a name='GetLastSound'></a>
<h3 class='function'>
GetLastSound
</h3>
<pre class='funcdef'><span class='retname'>volume, position = </span>GetLastSound(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">volume</span> <span
class="argtype">(number)</span> – Volume of loudest sound played last
frame<br/> <span class="retname">position</span> <span
class="argtype">(table)</span> – World position of loudest sound played
last frame<br/>
<p><p>
</p>
<pre class='example'>
local vol, pos = GetLastSound()

</pre>
<hr/>
<a name='IsPointInWater'></a>
<h3 class='function'>
IsPointInWater
</h3>
<pre class='funcdef'><span class='retname'>inWater, depth = </span>IsPointInWater(<span class='argname'>point</span>)</pre>
<p>
Аргументы<br/> <span class="argname">point</span> <span
class="argtype">(table)</span> – World point as vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">inWater</span> <span
class="argtype">(boolean)</span> – True if point is in water<br/> <span
class="retname">depth</span> <span class="argtype">(number)</span> –
Depth of point into water, or zero if not in water<br/>
<p><p>
</p>
<pre class='example'>
local wet, d = IsPointInWater(Vec(10, 0, 0))
if wet then
    ...point d meters into water
end

</pre>
<hr/>
<a name='Shoot'></a>
<h3 class='function'>
Shoot
</h3>
<pre class='funcdef'><span class='retname'></span>Shoot(<span class='argname'>origin, direction, [type]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">origin</span> <span
class="argtype">(table)</span> – Origin in world space as vector<br/>
<span class="argname">direction</span> <span
class="argtype">(table)</span> – Unit length direction as world space
vector<br/> <span class="argname">type</span> <span
class="argtype">(number, optional)</span> – 0 is regular bullet
(default) and 1 is rocket<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Shoot bullet or rocket (used for chopper)
<p>
</p>
<pre class='example'>
Shoot(Vec(0, 10, 0), Vec(0, 0, 1))

</pre>
<hr/>
<a name='MakeHole'></a>
<h3 class='function'>
MakeHole
</h3>
<pre class='funcdef'><span class='retname'></span>MakeHole(<span class='argname'>position, r0, [r1], [r2], [silent]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">position</span> <span
class="argtype">(table)</span> – Hole center point<br/> <span
class="argname">r0</span> <span class="argtype">(number)</span> – Hole
radius for soft materials<br/> <span class="argname">r1</span> <span
class="argtype">(number, optional)</span> – Hole radius for medium
materials. May not be bigger than r0. Default zero.<br/> <span
class="argname">r2</span> <span class="argtype">(number,
optional)</span> – Hole radius for hard materials. May not be bigger
than r1. Default zero.<br/> <span class="argname">silent</span> <span
class="argtype">(boolean, optional)</span> – Make hole without playing
any break sounds.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Make a hole in the environment. Radius is given in meters. Soft
materials: glass, foliage, dirt, wood, plaster and plastic. Medium
materials: concrete, brick and weak metal. Hard materials: hard metal
and hard masonry.
<p>
</p>
<pre class='example'>
MakeHole(pos, 1.2, 1.0)

</pre>
<hr/>
<a name='Explosion'></a>
<h3 class='function'>
Explosion
</h3>
<pre class='funcdef'><span class='retname'></span>Explosion(<span class='argname'>pos, size</span>)</pre>
<p>
Аргументы<br/> <span class="argname">pos</span> <span
class="argtype">(table)</span> – Position in world space as vector<br/>
<span class="argname">size</span> <span class="argtype">(number)</span>
– Explosion size from 0.5 to 4.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
Explosion(Vec(0, 10, 0), 1)

</pre>
<hr/>
<a name='SpawnParticle'></a>
<h3 class='function'>
SpawnParticle
</h3>
<pre class='funcdef'><span class='retname'></span>SpawnParticle(<span class='argname'>type, origin, velocity, size, life</span>)</pre>
<p>
Аргументы<br/> <span class="argname">type</span> <span
class="argtype">(string)</span> – Type of particle: "smoke",
"darksmoke", "fire" or "water"<br/> <span class="argname">origin</span>
<span class="argtype">(table)</span> – Origon in world space as
vector<br/> <span class="argname">velocity</span> <span
class="argtype">(table)</span> – Velocity in world space as vector
(m/s)<br/> <span class="argname">size</span> <span
class="argtype">(number)</span> – Size of particle (meters)<br/> <span
class="argname">life</span> <span class="argtype">(number)</span> –
Lifetime of particle (seconds)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SpawnParticle("smoke", Vec(0, 10, 0), Vec(0, 1, 0), 2, 5)

</pre>
<hr/>
<a name='SpawnFire'></a>
<h3 class='function'>
SpawnFire
</h3>
<pre class='funcdef'><span class='retname'></span>SpawnFire(<span class='argname'>pos</span>)</pre>
<p>
Аргументы<br/> <span class="argname">pos</span> <span
class="argtype">(table)</span> – Position in world space as vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
SpawnFire(Vec(0, 10, 0))

</pre>
<hr/>
<a name='GetFireCount'></a>
<h3 class='function'>
GetFireCount
</h3>
<pre class='funcdef'><span class='retname'>count = </span>GetFireCount(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">count</span> <span
class="argtype">(number)</span> – Number of active fires in level<br/>
<p><p>
</p>
<pre class='example'>
local c = GetFireCount()

</pre>
<hr/>
<a name='GetCameraTransform'></a>
<h3 class='function'>
GetCameraTransform
</h3>
<pre class='funcdef'><span class='retname'>transform = </span>GetCameraTransform(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">transform</span> <span
class="argtype">(table)</span> – Current camera transform<br/>
<p><p>
</p>
<pre class='example'>
local t = GetCameraTransform()

</pre>
<hr/>
<a name='SetCameraTransform'></a>
<h3 class='function'>
SetCameraTransform
</h3>
<pre class='funcdef'><span class='retname'></span>SetCameraTransform(<span class='argname'>transform, [fov]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">transform</span> <span
class="argtype">(table)</span> – Desired camera transform<br/> <span
class="argname">fov</span> <span class="argtype">(number,
optional)</span> – Optional horizontal field of view in degrees
(default: 90)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Override current camera transform for this frame. Call continuously to
keep overriding.
<p>
</p>
<pre class='example'>
SetCameraTransform(Transform(Vec(0, 10, 0), QuatEuler(0, 90, 0)))

</pre>
<hr/>
<a name='PointLight'></a>
<h3 class='function'>
PointLight
</h3>
<pre class='funcdef'><span class='retname'></span>PointLight(<span class='argname'>pos, r, g, b, [intensity]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">pos</span> <span
class="argtype">(table)</span> – World space light position<br/> <span
class="argname">r</span> <span class="argtype">(number)</span> –
Red<br/> <span class="argname">g</span> <span
class="argtype">(number)</span> – Green<br/> <span
class="argname">b</span> <span class="argtype">(number)</span> –
Blue<br/> <span class="argname">intensity</span> <span
class="argtype">(number, optional)</span> – Intensity. Default is
1.0.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Add a temporary point light to the world for this frame. Call
continuously for a steady light.
<p>
</p>
<pre class='example'>
--Pulsating, yellow light above world origo
local intensity = 3 + math.sin(GetTime())
PointLight(Vec(0, 5, 0), 1, 1, 0, intensity)

</pre>
<hr/>
<a name='SetTimeScale'></a>
<h3 class='function'>
SetTimeScale
</h3>
<pre class='funcdef'><span class='retname'></span>SetTimeScale(<span class='argname'>scale</span>)</pre>
<p>
Аргументы<br/> <span class="argname">scale</span> <span
class="argtype">(number)</span> – Time scale 0.1 to 1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Experimental. Scale time in order to make a slow-motion effect. Audio
will also be affected. Note that this will affect physics behavior and
is not intended for gameplay purposes. Calling this function will slow
down time for the next frame only. Call every frame from tick function
to get steady slow-motion.
<p>
</p>
<pre class='example'>
--Slow down time when holding down a key
if InputDown('t') then
    SetTimeScale(0.2)
end

</pre>
<hr/>
<a name='DrawLine'></a>
<h3 class='function'>
DrawLine
</h3>
<pre class='funcdef'><span class='retname'></span>DrawLine(<span class='argname'>p0, p1, [r], [g], [b], [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">p0</span> <span
class="argtype">(table)</span> – World space point as vector<br/> <span
class="argname">p1</span> <span class="argtype">(table)</span> – World
space point as vector<br/> <span class="argname">r</span> <span
class="argtype">(number, optional)</span> – Red<br/> <span
class="argname">g</span> <span class="argtype">(number, optional)</span>
– Green<br/> <span class="argname">b</span> <span
class="argtype">(number, optional)</span> – Blue<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Draw a 3D line. In contrast to DrawDebugLine, it will not show behind
objects. Default color is white.
<p>
</p>
<pre class='example'>
--Draw white debug line
DrawLine(Vec(0, 0, 0), Vec(-10, 5, -10))

--Draw red debug line
DrawLine(Vec(0, 0, 0), Vec(10, 5, 10), 1, 0, 0)

</pre>
<hr/>
<a name='DebugLine'></a>
<h3 class='function'>
DebugLine
</h3>
<pre class='funcdef'><span class='retname'></span>DebugLine(<span class='argname'>p0, p1, [r], [g], [b], [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">p0</span> <span
class="argtype">(table)</span> – World space point as vector<br/> <span
class="argname">p1</span> <span class="argtype">(table)</span> – World
space point as vector<br/> <span class="argname">r</span> <span
class="argtype">(number, optional)</span> – Red<br/> <span
class="argname">g</span> <span class="argtype">(number, optional)</span>
– Green<br/> <span class="argname">b</span> <span
class="argtype">(number, optional)</span> – Blue<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Draw a 3D debug overlay line in the world. Default color is white.
<p>
</p>
<pre class='example'>
--Draw white debug line
DebugLine(Vec(0, 0, 0), Vec(-10, 5, -10))

--Draw red debug line
DebugLine(Vec(0, 0, 0), Vec(10, 5, 10), 1, 0, 0)

</pre>
<hr/>
<a name='DebugCross'></a>
<h3 class='function'>
DebugCross
</h3>
<pre class='funcdef'><span class='retname'></span>DebugCross(<span class='argname'>p0, [r], [g], [b], [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">p0</span> <span
class="argtype">(table)</span> – World space point as vector<br/> <span
class="argname">r</span> <span class="argtype">(number, optional)</span>
– Red<br/> <span class="argname">g</span> <span class="argtype">(number,
optional)</span> – Green<br/> <span class="argname">b</span> <span
class="argtype">(number, optional)</span> – Blue<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Draw a debug cross in the world to highlight a location. Default color
is white.
<p>
</p>
<pre class='example'>
DebugCross(Vec(10, 5, 5))

</pre>
<hr/>
<a name='DebugWatch'></a>
<h3 class='function'>
DebugWatch
</h3>
<pre class='funcdef'><span class='retname'></span>DebugWatch(<span class='argname'>name, value</span>)</pre>
<p>
Аргументы<br/> <span class="argname">name</span> <span
class="argtype">(string)</span> – Name<br/> <span
class="argname">value</span> <span class="argtype">(string)</span> –
Value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Show a named valued on screen for debug purposes. Up to 32 values can be
shown simultaneously. Values updated the current frame are drawn opaque.
Old values are drawn transparent in white.
<p>
The function will also recognize vectors, quaternions and transforms as
second argument and convert them to strings automatically.
<p>
</p>
<pre class='example'>
local t = 5
DebugWatch("time", t)

</pre>
<hr/>
<a name='DebugPrint'></a>
<h3 class='function'>
DebugPrint
</h3>
<pre class='funcdef'><span class='retname'></span>DebugPrint(<span class='argname'>message</span>)</pre>
<p>
Аргументы<br/> <span class="argname">message</span> <span
class="argtype">(string)</span> – Message to display<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Display message on screen. The last 20 lines are displayed.
<p>
</p>
<pre class='example'>
DebugPrint("time")

</pre>
<hr/>
<a name='UiMakeInteractive'></a>
<h3 class='function'>
UiMakeInteractive
</h3>
<pre class='funcdef'><span class='retname'></span>UiMakeInteractive(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Calling this function will disable game input, bring up the mouse
pointer and allow Ui interaction with the calling script without pausing
the game. This can be useful to make interactive user interfaces from
scripts while the game is running. Call this continuously every frame as
long as Ui interaction is desired.
<p>
</p>
<pre class='example'>
UiMakeInteractive()

</pre>
<hr/>
<a name='UiPush'></a>
<h3 class='function'>
UiPush
</h3>
<pre class='funcdef'><span class='retname'></span>UiPush(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Push state onto stack. This is used in combination with UiPop to
remember a state and restore to that state later.
<p>
</p>
<pre class='example'>
UiColor(1,0,0)
UiText("Red")
UiPush()
    UiColor(0,1,0)
    UiText("Green")
UiPop()
UiText("Red")

</pre>
<hr/>
<a name='UiPop'></a>
<h3 class='function'>
UiPop
</h3>
<pre class='funcdef'><span class='retname'></span>UiPop(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Pop state from stack and make it the current one. This is used in
combination with UiPush to remember a previous state and go back to it
later.
<p>
</p>
<pre class='example'>
UiColor(1,0,0)
UiText("Red")
UiPush()
    UiColor(0,1,0)
    UiText("Green")
UiPop()
UiText("Red")

</pre>
<hr/>
<a name='UiWidth'></a>
<h3 class='function'>
UiWidth
</h3>
<pre class='funcdef'><span class='retname'>width = </span>UiWidth(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">width</span> <span
class="argtype">(number)</span> – Width of draw context<br/>
<p><p>
</p>
<pre class='example'>
local w = UiWidth()

</pre>
<hr/>
<a name='UiHeight'></a>
<h3 class='function'>
UiHeight
</h3>
<pre class='funcdef'><span class='retname'>height = </span>UiHeight(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">height</span> <span
class="argtype">(number)</span> – Height of draw context<br/>
<p><p>
</p>
<pre class='example'>
local h = UiHeight()

</pre>
<hr/>
<a name='UiCenter'></a>
<h3 class='function'>
UiCenter
</h3>
<pre class='funcdef'><span class='retname'>center = </span>UiCenter(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">center</span> <span
class="argtype">(number)</span> – Half width of draw context<br/>
<p><p>
</p>
<pre class='example'>
local c = UiCenter()
--Same as 
local c = UiWidth()/2

</pre>
<hr/>
<a name='UiMiddle'></a>
<h3 class='function'>
UiMiddle
</h3>
<pre class='funcdef'><span class='retname'>middle = </span>UiMiddle(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">middle</span> <span
class="argtype">(number)</span> – Half height of draw context<br/>
<p><p>
</p>
<pre class='example'>
local m = UiMiddle()
--Same as
local m = UiHeight()/2

</pre>
<hr/>
<a name='UiColor'></a>
<h3 class='function'>
UiColor
</h3>
<pre class='funcdef'><span class='retname'></span>UiColor(<span class='argname'>r, g, b, [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">r</span> <span
class="argtype">(number)</span> – Red channel<br/> <span
class="argname">g</span> <span class="argtype">(number)</span> – Green
channel<br/> <span class="argname">b</span> <span
class="argtype">(number)</span> – Blue channel<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha channel. Default 1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
--Set color yellow
UiColor(1,1,0)

</pre>
<hr/>
<a name='UiColorFilter'></a>
<h3 class='function'>
UiColorFilter
</h3>
<pre class='funcdef'><span class='retname'></span>UiColorFilter(<span class='argname'>r, g, b, [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">r</span> <span
class="argtype">(number)</span> – Red channel<br/> <span
class="argname">g</span> <span class="argtype">(number)</span> – Green
channel<br/> <span class="argname">b</span> <span
class="argtype">(number)</span> – Blue channel<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha channel. Default 1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Color filter, multiplied to all future colors in this scope
<p>
</p>
<pre class='example'>
UiPush()
    --Draw menu in transparent, yellow color tint
    UiColorFilter(1, 1, 0, 0.5)
    drawMenu()
UiPop()

</pre>
<hr/>
<a name='UiTranslate'></a>
<h3 class='function'>
UiTranslate
</h3>
<pre class='funcdef'><span class='retname'></span>UiTranslate(<span class='argname'>x, y</span>)</pre>
<p>
Аргументы<br/> <span class="argname">x</span> <span
class="argtype">(number)</span> – X component<br/> <span
class="argname">y</span> <span class="argtype">(number)</span> – Y
component<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Translate cursor
<p>
</p>
<pre class='example'>
UiPush()
    UiTranslate(100, 0)
    UiText("Indented")
UiPop()

</pre>
<hr/>
<a name='UiRotate'></a>
<h3 class='function'>
UiRotate
</h3>
<pre class='funcdef'><span class='retname'></span>UiRotate(<span class='argname'>angle</span>)</pre>
<p>
Аргументы<br/> <span class="argname">angle</span> <span
class="argtype">(number)</span> – Angle in degrees, counter
clockwise<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Rotate cursor
<p>
</p>
<pre class='example'>
UiPush()
    UiRotate(45)
    UiText("Rotated")
UiPop()

</pre>
<hr/>
<a name='UiScale'></a>
<h3 class='function'>
UiScale
</h3>
<pre class='funcdef'><span class='retname'></span>UiScale(<span class='argname'>x, [y]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">x</span> <span
class="argtype">(number)</span> – X component<br/> <span
class="argname">y</span> <span class="argtype">(number, optional)</span>
– Y component. Default value is x.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Scale cursor either uniformly (one argument) or non-uniformly (two
arguments)
<p>
</p>
<pre class='example'>
UiPush()
    UiScale(2)
    UiText("Double size")
UiPop()

</pre>
<hr/>
<a name='UiWindow'></a>
<h3 class='function'>
UiWindow
</h3>
<pre class='funcdef'><span class='retname'></span>UiWindow(<span class='argname'>width, height, [clip]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">width</span> <span
class="argtype">(number)</span> – Window width<br/> <span
class="argname">height</span> <span class="argtype">(number)</span> –
Window height<br/> <span class="argname">clip</span> <span
class="argtype">(boolean, optional)</span> – Clip content outside
window. Default is false.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Set up new bounds. Calls to UiWidth, UiHeight, UiCenter and UiMiddle
will operate in the context of the window size. If clip is set to true,
contents of window will be clipped to bounds (only works properly for
non-rotated windows).
<p>
</p>
<pre class='example'>
UiPush()
    UiWindow(400, 200)
    local w = UiWidth()
    --w is now 400
UiPop()

</pre>
<hr/>
<a name='UiSafeMargins'></a>
<h3 class='function'>
UiSafeMargins
</h3>
<pre class='funcdef'><span class='retname'>x0, y0, x1, y1 = </span>UiSafeMargins(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">x0</span> <span
class="argtype">(number)</span> – Left<br/> <span
class="retname">y0</span> <span class="argtype">(number)</span> –
Top<br/> <span class="retname">x1</span> <span
class="argtype">(number)</span> – Right<br/> <span
class="retname">y1</span> <span class="argtype">(number)</span> –
Bottom<br/>
<p>
Return a safe drawing area that will always be visible regardless of
display aspect ratio. The safe drawing area will always be 1920 by 1080
in size. This is useful for setting up a fixed size UI.
<p>
</p>
<pre class='example'>
function draw()
    local x0, y0, x1, y1 = UiSafeMargins()
    UiTranslate(x0, y0)
    UiWindow(x1-x0, y1-y0, true)
    --The drawing area is now 1920 by 1080 in the center of screen
    drawMenu()
end

</pre>
<hr/>
<a name='UiAlign'></a>
<h3 class='function'>
UiAlign
</h3>
<pre class='funcdef'><span class='retname'></span>UiAlign(<span class='argname'>alignment</span>)</pre>
<p>
Аргументы<br/> <span class="argname">alignment</span> <span
class="argtype">(string)</span> – Alignment keywords<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
The alignment determines how content is aligned with respect to the
cursor.
<table border=0><tr><td class='header'>
 Alignment 
</td><td class='header'>
 Описание
</td></tr>
<tr><td class='first' valign='top'>
left
</td><td valign='top'> 
Horizontally align to the left
</td></tr><tr><td class='first' valign='top'>
right
</td><td valign='top'> 
Horizontally align to the right
</td></tr><tr><td class='first' valign='top'>
center
</td><td valign='top'> 
Horizontally align to the center
</td></tr><tr><td class='first' valign='top'>
top
</td><td valign='top'> 
Vertically align to the top
</td></tr><tr><td class='first' valign='top'>
bottom
</td><td valign='top'> 
Veritcally align to the bottom
</td></tr><tr><td class='first' valign='top'>
middle
</td><td valign='top'> 
Vertically align to the middle
</td></tr><table/>
Alignment can contain combinations of these, for instance: "center
middle", "left top", "center top", etc. If horizontal or vertical
alginment is omitted it will depend on the element drawn. Text, for
instance has default vertical alignment at baseline.
<p>
<p>
</p>
<pre class='example'>
UiAlign("left")
UiText("Aligned left at baseline")

UiAlign("center middle")
UiText("Fully centered")

</pre>
<hr/>
<a name='UiModalBegin'></a>
<h3 class='function'>
UiModalBegin
</h3>
<pre class='funcdef'><span class='retname'></span>UiModalBegin(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Disable input for everything, except what's between UiModalBegin and
UiModalEnd (or if modal state is popped)
<p>
</p>
<pre class='example'>
UiModalBegin()
if UiTextButton("Okay") then
    --All other interactive ui elements except this one are disabled
end
UiModalEnd()

--This is also okay
UiPush()
    UiModalBegin()
    if UiTextButton("Okay") then
        --All other interactive ui elements except this one are disabled
    end
UiPop()
--No longer modal

</pre>
<hr/>
<a name='UiModalEnd'></a>
<h3 class='function'>
UiModalEnd
</h3>
<pre class='funcdef'><span class='retname'></span>UiModalEnd(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Disable input for everything, except what's between UiModalBegin and
UiModalEnd Calling this function is optional. Modality is part of the
current state and will be lost if modal state is popped.
<p>
</p>
<pre class='example'>
UiModalBegin()
if UiTextButton("Okay") then
    --All other interactive ui elements except this one are disabled
end
UiModalEnd()

</pre>
<hr/>
<a name='UiDisableInput'></a>
<h3 class='function'>
UiDisableInput
</h3>
<pre class='funcdef'><span class='retname'></span>UiDisableInput(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Disable input
<p>
</p>
<pre class='example'>
UiPush()
    UiDisableInput()
    if UiButtonText("Okay") then
        --Will never happen
    end
UiPop()

</pre>
<hr/>
<a name='UiEnableInput'></a>
<h3 class='function'>
UiEnableInput
</h3>
<pre class='funcdef'><span class='retname'></span>UiEnableInput(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Enable input that has been previously disabled
<p>
</p>
<pre class='example'>
UiDisableInput()
if UiButtonText("Okay") then
    --Will never happen
end

UiEnableInput()
if UiButtonText("Okay") then
    --This can happen
end

</pre>
<hr/>
<a name='UiReceivesInput'></a>
<h3 class='function'>
UiReceivesInput
</h3>
<pre class='funcdef'><span class='retname'>receives = </span>UiReceivesInput(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">receives</span> <span
class="argtype">(boolean)</span> – True if current context receives
input<br/>
<p>
This function will check current state receives input. This is the case
if input is not explicitly disabled with (with UiDisableInput) and no
other state is currently modal (with UiModalBegin). Input functions and
UI elements already do this check internally, but it can sometimes be
useful to read the input state manually to trigger things in the UI.
<p>
</p>
<pre class='example'>
if UiReceivesInput() then
    highlightItemAtMousePointer()
end

</pre>
<hr/>
<a name='UiGetMousePos'></a>
<h3 class='function'>
UiGetMousePos
</h3>
<pre class='funcdef'><span class='retname'>x, y = </span>UiGetMousePos(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">x</span> <span
class="argtype">(number)</span> – X coordinate<br/> <span
class="retname">y</span> <span class="argtype">(number)</span> – Y
coordinate<br/>
<p>
Get mouse pointer position relative to the cursor
<p>
</p>
<pre class='example'>
local x, y = UiGetMousePos()

</pre>
<hr/>
<a name='UiIsMouseInRect'></a>
<h3 class='function'>
UiIsMouseInRect
</h3>
<pre class='funcdef'><span class='retname'>inside = </span>UiIsMouseInRect(<span class='argname'>w, h</span>)</pre>
<p>
Аргументы<br/> <span class="argname">w</span> <span
class="argtype">(number)</span> – Width<br/> <span
class="argname">h</span> <span class="argtype">(number)</span> –
Height<br/>
<p>
Возвращаемое значение<br/> <span class="retname">inside</span> <span
class="argtype">(boolean)</span> – True if mouse pointer is within
rectangle<br/>
<p>
Check if mouse pointer is within rectangle. Note that this function
respects alignment.
<p>
</p>
<pre class='example'>
if UiIsMouseInRect(100, 100) then
    -- mouse pointer is in rectangle
end

</pre>
<hr/>
<a name='UiWorldToPixel'></a>
<h3 class='function'>
UiWorldToPixel
</h3>
<pre class='funcdef'><span class='retname'>x, y, distance = </span>UiWorldToPixel(<span class='argname'>point</span>)</pre>
<p>
Аргументы<br/> <span class="argname">point</span> <span
class="argtype">(table)</span> – 3D world position as vector<br/>
<p>
Возвращаемое значение<br/> <span class="retname">x</span> <span
class="argtype">(number)</span> – X coordinate<br/> <span
class="retname">y</span> <span class="argtype">(number)</span> – Y
coordinate<br/> <span class="retname">distance</span> <span
class="argtype">(number)</span> – Distance to point<br/>
<p>
Convert world space position to user interface X and Y coordinate
relative to the cursor. The distance is in meters and positive if in
front of camera, negative otherwise.
<p>
</p>
<pre class='example'>
local x, y, dist = UiWorldToPixel(point)
if dist > 0 then
UiTranslate(x, y)
UiText("Label")
end

</pre>
<hr/>
<a name='UiPixelToWorld'></a>
<h3 class='function'>
UiPixelToWorld
</h3>
<pre class='funcdef'><span class='retname'>direction = </span>UiPixelToWorld(<span class='argname'>x, y</span>)</pre>
<p>
Аргументы<br/> <span class="argname">x</span> <span
class="argtype">(number)</span> – X coordinate<br/> <span
class="argname">y</span> <span class="argtype">(number)</span> – Y
coordinate<br/>
<p>
Возвращаемое значение<br/> <span class="retname">direction</span> <span
class="argtype">(table)</span> – 3D world direction as vector<br/>
<p>
Convert X and Y UI coordinate to a world direction, as seen from current
camera. This can be used to raycast into the scene from the mouse
pointer position.
<p>
</p>
<pre class='example'>
UiMakeInteractive()
local x, y = UiGetMousePos()
local dir = UiPixelToWorld(x, y)
local pos = GetCameraTransform().pos
local hit, dist = QueryRaycast(pos, dir, 100)
if hit then
    DebugPrint("hit distance: " .. dist)
end

</pre>
<hr/>
<a name='UiBlur'></a>
<h3 class='function'>
UiBlur
</h3>
<pre class='funcdef'><span class='retname'></span>UiBlur(<span class='argname'>amount</span>)</pre>
<p>
Аргументы<br/> <span class="argname">amount</span> <span
class="argtype">(number)</span> – Blur amount (0.0 to 1.0)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Perform a gaussian blur on current screen content
<p>
</p>
<pre class='example'>
UiBlur(1.0)
drawMenu()

</pre>
<hr/>
<a name='UiFont'></a>
<h3 class='function'>
UiFont
</h3>
<pre class='funcdef'><span class='retname'></span>UiFont(<span class='argname'>path, size</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to TTF font file<br/> <span
class="argname">size</span> <span class="argtype">(number)</span> – Font
size (10 to 100)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
UiFont("bold.ttf", 24)
UiText("Hello")

</pre>
<hr/>
<a name='UiFontHeight'></a>
<h3 class='function'>
UiFontHeight
</h3>
<pre class='funcdef'><span class='retname'>size = </span>UiFontHeight(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">size</span> <span
class="argtype">(number)</span> – Font size<br/>
<p><p>
</p>
<pre class='example'>
local h = UiFontHeight()

</pre>
<hr/>
<a name='UiText'></a>
<h3 class='function'>
UiText
</h3>
<pre class='funcdef'><span class='retname'>w, h = </span>UiText(<span class='argname'>text, [move]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">text</span> <span
class="argtype">(string)</span> – Print text at cursor location<br/>
<span class="argname">move</span> <span class="argtype">(boolean,
optional)</span> – Automatically move cursor vertically. Default
false.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">w</span> <span
class="argtype">(number)</span> – Width of text<br/> <span
class="retname">h</span> <span class="argtype">(number)</span> – Height
of text<br/>
<p><p>
</p>
<pre class='example'>
UiFont("bold.ttf", 24)
UiText("Hello")

...

--Automatically advance cursor
UiText("First line", true)
UiText("Second line", true)

</pre>
<hr/>
<a name='UiGetTextSize'></a>
<h3 class='function'>
UiGetTextSize
</h3>
<pre class='funcdef'><span class='retname'>w, h = </span>UiGetTextSize(<span class='argname'>text</span>)</pre>
<p>
Аргументы<br/> <span class="argname">text</span> <span
class="argtype">(string)</span> – A text string<br/>
<p>
Возвращаемое значение<br/> <span class="retname">w</span> <span
class="argtype">(number)</span> – Width of text<br/> <span
class="retname">h</span> <span class="argtype">(number)</span> – Height
of text<br/>
<p><p>
</p>
<pre class='example'>

local w, h = GetTextSize("Some text")

</pre>
<hr/>
<a name='UiWordWrap'></a>
<h3 class='function'>
UiWordWrap
</h3>
<pre class='funcdef'><span class='retname'></span>UiWordWrap(<span class='argname'>width</span>)</pre>
<p>
Аргументы<br/> <span class="argname">width</span> <span
class="argtype">(number)</span> – Maximum width of text<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
UiWordWrap(200)
UiText("Some really long text that will get wrapped into several lines")

</pre>
<hr/>
<a name='UiTextOutline'></a>
<h3 class='function'>
UiTextOutline
</h3>
<pre class='funcdef'><span class='retname'></span>UiTextOutline(<span class='argname'>r, g, b, a, [thickness]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">r</span> <span
class="argtype">(number)</span> – Red channel<br/> <span
class="argname">g</span> <span class="argtype">(number)</span> – Green
channel<br/> <span class="argname">b</span> <span
class="argtype">(number)</span> – Blue channel<br/> <span
class="argname">a</span> <span class="argtype">(number)</span> – Alpha
channel<br/> <span class="argname">thickness</span> <span
class="argtype">(number, optional)</span> – Outline thickness. Default
is 0.1<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
--Black outline, standard thickness
UiTextOutline(0,0,0,1)
UiText("Text with outline")

</pre>
<hr/>
<a name='UiTextShadow'></a>
<h3 class='function'>
UiTextShadow
</h3>
<pre class='funcdef'><span class='retname'></span>UiTextShadow(<span class='argname'>r, g, b, a, [distance], [blur]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">r</span> <span
class="argtype">(number)</span> – Red channel<br/> <span
class="argname">g</span> <span class="argtype">(number)</span> – Green
channel<br/> <span class="argname">b</span> <span
class="argtype">(number)</span> – Blue channel<br/> <span
class="argname">a</span> <span class="argtype">(number)</span> – Alpha
channel<br/> <span class="argname">distance</span> <span
class="argtype">(number, optional)</span> – Shadow distance. Default is
1.0<br/> <span class="argname">blur</span> <span
class="argtype">(number, optional)</span> – Shadow blur. Default is
0.5<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p><p>
</p>
<pre class='example'>
--Black drop shadow, 50% transparent, distance 2
UiTextShadow(0, 0, 0, 0.5, 2.0)
UiText("Text with drop shadow")

</pre>
<hr/>
<a name='UiRect'></a>
<h3 class='function'>
UiRect
</h3>
<pre class='funcdef'><span class='retname'></span>UiRect(<span class='argname'>w, h</span>)</pre>
<p>
Аргументы<br/> <span class="argname">w</span> <span
class="argtype">(number)</span> – Width<br/> <span
class="argname">h</span> <span class="argtype">(number)</span> –
Height<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Draw solid rectangle at cursor position
<p>
</p>
<pre class='example'>
--Draw full-screen black rectangle
UiColor(0, 0, 0)
UiRect(UiWidth(), UiHeight())

--Draw smaller, red, rotating rectangle in center of screen
UiPush()
    UiColor(1, 0, 0)
    UiTranslate(UiCenter(), UiMiddle())
    UiRotate(GetTime())
    UiAlign("center middle")
    UiRect(100, 100)
UiPop()

</pre>
<hr/>
<a name='UiImage'></a>
<h3 class='function'>
UiImage
</h3>
<pre class='funcdef'><span class='retname'>w, h = </span>UiImage(<span class='argname'>path</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to image (PNG or JPG format)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">w</span> <span
class="argtype">(number)</span> – Image width<br/> <span
class="retname">h</span> <span class="argtype">(number)</span> – Image
height<br/>
<p>
Draw image at cursor position
<p>
</p>
<pre class='example'>
--Draw image in center of screen
UiPush()
    UiTranslate(UiCenter(), UiMiddle())
    UiAlign("center middle")
    UiImage("test.png")
UiPop()

</pre>
<hr/>
<a name='UiGetImageSize'></a>
<h3 class='function'>
UiGetImageSize
</h3>
<pre class='funcdef'><span class='retname'>w, h = </span>UiGetImageSize(<span class='argname'>path</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to image (PNG or JPG format)<br/>
<p>
Возвращаемое значение<br/> <span class="retname">w</span> <span
class="argtype">(number)</span> – Image width<br/> <span
class="retname">h</span> <span class="argtype">(number)</span> – Image
height<br/>
<p>
Get image size
<p>
</p>
<pre class='example'>
local w,h = UiGetImageSize("test.png")

</pre>
<hr/>
<a name='UiImageBox'></a>
<h3 class='function'>
UiImageBox
</h3>
<pre class='funcdef'><span class='retname'></span>UiImageBox(<span class='argname'>path, width, height, borderWidth, borderHeight</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to image (PNG or JPG format)<br/>
<span class="argname">width</span> <span class="argtype">(number)</span>
– Width<br/> <span class="argname">height</span> <span
class="argtype">(number)</span> – Height<br/> <span
class="argname">borderWidth</span> <span class="argtype">(number)</span>
– Border width<br/> <span class="argname">borderHeight</span> <span
class="argtype">(number)</span> – Border height<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Draw 9-slice image at cursor position. Width should be at least
2*borderWidth. Height should be at least 2*borderHeight.
<p>
</p>
<pre class='example'>
UiImageBox("menu-frame.png", 200, 200, 10, 10)

</pre>
<hr/>
<a name='UiSound'></a>
<h3 class='function'>
UiSound
</h3>
<pre class='funcdef'><span class='retname'></span>UiSound(<span class='argname'>path, [volume], [pitch], [pan]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to sound file (OGG format)<br/>
<span class="argname">volume</span> <span class="argtype">(number,
optional)</span> – Playback volume. Default 1.0<br/> <span
class="argname">pitch</span> <span class="argtype">(number,
optional)</span> – Playback pitch. Default 1.0<br/> <span
class="argname">pan</span> <span class="argtype">(number,
optional)</span> – Playback stereo panning (-1.0 to 1.0). Default
0.0.<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
UI sounds are not affected by acoustics simulation. Use LoadSound /
PlaySound for that.
<p>
</p>
<pre class='example'>
UiSound("click.ogg")

</pre>
<hr/>
<a name='UiSoundLoop'></a>
<h3 class='function'>
UiSoundLoop
</h3>
<pre class='funcdef'><span class='retname'></span>UiSoundLoop(<span class='argname'>path, [volume]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to looping sound file (OGG
format)<br/> <span class="argname">volume</span> <span
class="argtype">(number, optional)</span> – Playback volume. Default
1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Call this continuously to keep playing loop. UI sounds are not affected
by acoustics simulation. Use LoadLoop / PlayLoop for that.
<p>
</p>
<pre class='example'>
if animating then
    UiSoundLoop("screech.ogg")
end

</pre>
<hr/>
<a name='UiMute'></a>
<h3 class='function'>
UiMute
</h3>
<pre class='funcdef'><span class='retname'></span>UiMute(<span class='argname'>amount, [music]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">amount</span> <span
class="argtype">(number)</span> – Mute by this amount (0.0 to 1.0)<br/>
<span class="argname">music</span> <span class="argtype">(boolean,
optional)</span> – Mute music as well<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Mute game audio and optionally music for the next frame. Call
continuously to stay muted.
<p>
</p>
<pre class='example'>
if menuOpen then
    UiMute(1.0)
end

</pre>
<hr/>
<a name='UiButtonImageBox'></a>
<h3 class='function'>
UiButtonImageBox
</h3>
<pre class='funcdef'><span class='retname'></span>UiButtonImageBox(<span class='argname'>path, borderWidth, borderHeight, [r], [g], [b], [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(string)</span> – Path to image (PNG or JPG format)<br/>
<span class="argname">borderWidth</span> <span
class="argtype">(number)</span> – Border width<br/> <span
class="argname">borderHeight</span> <span
class="argtype">(number)</span> – Border height<br/> <span
class="argname">r</span> <span class="argtype">(number, optional)</span>
– Red multiply. Default 1.0<br/> <span class="argname">g</span> <span
class="argtype">(number, optional)</span> – Green multiply. Default
1.0<br/> <span class="argname">b</span> <span class="argtype">(number,
optional)</span> – Blue multiply. Default 1.0<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha channel. Default 1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Set up 9-slice image to be used as background for buttons.
<p>
</p>
<pre class='example'>
UiButtonImageBox("button-9slice.png", 10, 10)
if UiTextButton("Test") then
    ...
end

</pre>
<hr/>
<a name='UiButtonHoverColor'></a>
<h3 class='function'>
UiButtonHoverColor
</h3>
<pre class='funcdef'><span class='retname'></span>UiButtonHoverColor(<span class='argname'>r, g, b, [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">r</span> <span
class="argtype">(number)</span> – Red multiply<br/> <span
class="argname">g</span> <span class="argtype">(number)</span> – Green
multiply<br/> <span class="argname">b</span> <span
class="argtype">(number)</span> – Blue multiply<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha channel. Default 1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Button color filter when hovering mouse pointer.
<p>
</p>
<pre class='example'>
UiButtonHoverColor(1, 0, 0)
if UiTextButton("Test") then
    ...
end

</pre>
<hr/>
<a name='UiButtonPressColor'></a>
<h3 class='function'>
UiButtonPressColor
</h3>
<pre class='funcdef'><span class='retname'></span>UiButtonPressColor(<span class='argname'>r, g, b, [a]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">r</span> <span
class="argtype">(number)</span> – Red multiply<br/> <span
class="argname">g</span> <span class="argtype">(number)</span> – Green
multiply<br/> <span class="argname">b</span> <span
class="argtype">(number)</span> – Blue multiply<br/> <span
class="argname">a</span> <span class="argtype">(number, optional)</span>
– Alpha channel. Default 1.0<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
Button color filter when pressing down.
<p>
</p>
<pre class='example'>
UiButtonPressColor(0, 1, 0)
if UiTextButton("Test") then
    ...
end

</pre>
<hr/>
<a name='UiButtonPressDist'></a>
<h3 class='function'>
UiButtonPressDist
</h3>
<pre class='funcdef'><span class='retname'></span>UiButtonPressDist(<span class='argname'>dist</span>)</pre>
<p>
Аргументы<br/> <span class="argname">dist</span> <span
class="argtype">(number)</span> – Press distance<br/>
<p>
Возвращаемое значение<br/> <span class="retname">none</span>
<p>
The button offset when being pressed
<p>
</p>
<pre class='example'>
UiButtonPressDistance(4)
if UiTextButton("Test") then
    ...
end

</pre>
<hr/>
<a name='UiTextButton'></a>
<h3 class='function'>
UiTextButton
</h3>
<pre class='funcdef'><span class='retname'>pressed = </span>UiTextButton(<span class='argname'>text, [w], [h]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">text</span> <span
class="argtype">(string)</span> – Text on button<br/> <span
class="argname">w</span> <span class="argtype">(number, optional)</span>
– Button width<br/> <span class="argname">h</span> <span
class="argtype">(number, optional)</span> – Button height<br/>
<p>
Возвращаемое значение<br/> <span class="retname">pressed</span> <span
class="argtype">(boolean)</span> – True if user clicked button<br/>
<p><p>
</p>
<pre class='example'>
if UiTextButton("Test") then
    ...
end

</pre>
<hr/>
<a name='UiImageButton'></a>
<h3 class='function'>
UiImageButton
</h3>
<pre class='funcdef'><span class='retname'>pressed = </span>UiImageButton(<span class='argname'>path, [w], [h]</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(number)</span> – Image path (PNG or JPG file)<br/>
<span class="argname">w</span> <span class="argtype">(number,
optional)</span> – Button width<br/> <span class="argname">h</span>
<span class="argtype">(number, optional)</span> – Button height<br/>
<p>
Возвращаемое значение<br/> <span class="retname">pressed</span> <span
class="argtype">(boolean)</span> – True if user clicked button<br/>
<p><p>
</p>
<pre class='example'>
if UiImageButton("image.png") then
    ...
end

</pre>
<hr/>
<a name='UiBlankButton'></a>
<h3 class='function'>
UiBlankButton
</h3>
<pre class='funcdef'><span class='retname'>pressed = </span>UiBlankButton(<span class='argname'>w, h</span>)</pre>
<p>
Аргументы<br/> <span class="argname">w</span> <span
class="argtype">(number)</span> – Button width<br/> <span
class="argname">h</span> <span class="argtype">(number)</span> – Button
height<br/>
<p>
Возвращаемое значение<br/> <span class="retname">pressed</span> <span
class="argtype">(boolean)</span> – True if user clicked button<br/>
<p><p>
</p>
<pre class='example'>
if UiBlankButton(30, 30) then
    ...
end

</pre>
<hr/>
<a name='UiSlider'></a>
<h3 class='function'>
UiSlider
</h3>
<pre class='funcdef'><span class='retname'>value, done = </span>UiSlider(<span class='argname'>path, axis, current, min, max</span>)</pre>
<p>
Аргументы<br/> <span class="argname">path</span> <span
class="argtype">(number)</span> – Image path (PNG or JPG file)<br/>
<span class="argname">axis</span> <span class="argtype">(string)</span>
– Drag axis, must be "x" or "y"<br/> <span
class="argname">current</span> <span class="argtype">(number)</span> –
Current value<br/> <span class="argname">min</span> <span
class="argtype">(number)</span> – Minimum value<br/> <span
class="argname">max</span> <span class="argtype">(number)</span> –
Maximum value<br/>
<p>
Возвращаемое значение<br/> <span class="retname">value</span> <span
class="argtype">(number)</span> – New value, same as current if not
changed<br/> <span class="retname">done</span> <span
class="argtype">(boolean)</span> – True if user is finished changing
(released slider)<br/>
<p><p>
</p>
<pre class='example'>
value = UiSlider("dot.png", "x", value, 0, 100)

</pre>
<hr/>
<a name='UiGetScreen'></a>
<h3 class='function'>
UiGetScreen
</h3>
<pre class='funcdef'><span class='retname'>handle = </span>UiGetScreen(<span class='argname'></span>)</pre>
<p>
Аргументы<br/> <span class="argname">none</span>
<p>
Возвращаемое значение<br/> <span class="retname">handle</span> <span
class="argtype">(number)</span> – Handle to the screen running this
script or zero if none.<br/>
<p><p>
</p>
<pre class='example'>
--Turn off screen running current script
screen = UiGetScreen()
SetScreenEnabled(screen, false)

</pre>
<hr/>