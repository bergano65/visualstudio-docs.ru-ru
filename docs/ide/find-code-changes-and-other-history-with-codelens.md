---
title: "Поиск изменений кода и других журналов с помощью CodeLens | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 131
caps.handback.revision: 131
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Поиск изменений кода и других журналов с помощью CodeLens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Получайте дополнительные сведения о коде, не отрываясь от работы и не выходя из редактора. Находите ссылки на код, изменения кода, связанные ошибки, рабочие элементы, проверки кода и модульные тесты.  
  
> [!NOTE]
>  Средство CodeLens доступно только в выпусках Visual Studio Enterprise и Visual Studio Professional. Оно не доступно в выпуске Visual Studio Community.  
  
 Посмотрите, где и как отдельные части вашего кода используются в решении.  
  
 ![Индикаторы CodeLens в редакторе кода](../ide/media/codelensoverview.png "CodeLensOverview")  
  
 Сообщите рабочей группе об изменениях в коде, не выходя из редактора.  
  
 ![CodeLens &#45; обращение к команде](../ide/media/codelensovervew2.png "CodeLensOvervew2")  
  
 Чтобы выбрать, какие индикаторы должны отображаться, включить или выключить средство CodeLens, последовательно выберите пункты **Инструменты**, **Параметры**, **Текстовый редактор**, **Все языки**, **CodeLens**.  
  
##  <a name="FindReferences"></a> Поиск ссылок на код  
 Требуется:  
  
-   Visual Studio Enterprise или Visual Studio Professional  
  
-   Код Visual C\# .NET или Visual Basic .NET  
  
 Выберите индикатор **ссылок** \(**ALT \+ 2**\). Если в результатах отображается **0 ссылок**, это значит, что ссылки из кода Visual C\# или Visual Basic отсутствуют. Сюда не входят ссылки из других элементов, таких как XAML\- и ASPX\-файлы.  
  
 ![CodeLens &#45; выбор индикатора ссылок](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  
  
 Чтобы просмотреть код ссылки, наведите указатель мыши на ссылку.  
  
 ![CodeLens &#45; быстрый просмотр ссылки](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  
  
 Чтобы открыть файл, на который указывает ссылка, дважды щелкните эту ссылку.  
  
 Чтобы просмотреть отношения между этим кодом и его ссылками, [создайте карту кода](../modeling/map-dependencies-across-your-solutions.md) и выберите параметр **Показать все ссылки** в контекстном меню карты кода.  
  
 ![CodeLens &#45; ссылки на карте кода](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  
  
##  <a name="FindCodeHistory"></a> Поиск журнала кода и связанных элементов  
 Просмотрите журнал кода, чтобы узнать, что случилось. Можно также изучить изменения до их внедрения в ваш код, чтобы понять, как изменения в других ветвях могут повлиять на него.  
  
 Требуется:  
  
-   Visual Studio Enterprise или Visual Studio Professional  
  
-   Team Foundation Server 2013 или более поздней версии, Visual Studio Team Services или Git  
  
-   [Lync 2010 или более поздней версии или Skype для бизнеса](http://technet.microsoft.com/en-us/lync) \(для связи с коллегами, не выходя из редактора кода\)  
  
 Для кода на Visual C\# .NET или Visual Basic .NET, который хранится вместе с системой управления версиями Team Foundation \(TFVC\) или Git, сведения CodeLens предоставляются на уровнях класса и метода \(индикаторы *уровня кода элемента*\). Если репозиторий Git находится в TfGit, можно также получить ссылки на рабочие элементы TFS.  
  
 ![Индикаторы кода на уровне элемента](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  
  
 Для всех других типов файлов, которые можно открыть в редакторе Visual Studio, сведения о CodeLens по всему файлу приводятся в одном месте — в нижней части окна \(индикаторы *уровня файла*\).  
  
 ![Индикаторы CodeLens уровня файлов](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  
  
 Чтобы выбрать индикатор с помощью клавиатуры, нажмите и удерживайте клавишу **ALT** для отображения назначенных клавиш с цифрами.  
  
 ![Нажмите клавишу ALT для просмотра номеров доступа клавиатуры.](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  
  
### Поиск изменений в коде  
 Узнайте, кто изменил ваш код на C\# или Visual Basic, и просмотрите внесенные в код изменения на индикаторах уровня кода элемента. При использовании системы управления версиями Team Foundation \(TFVC\) в Team Foundation Server или Visual Studio Team Services отображается следующее.  
  
 ![CodeLens: получение журнала изменений для кода в TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  
  
 Период времени по умолчанию — последние 12 месяцев. Если код хранится в Team Foundation Server, это ограничение можно изменить, выполнив [команду TFSConfig](http://msdn.microsoft.com/ru-ru/94424190-3b6b-4f33-a6b6-5807f4225b62) вместе с [командой CodeIndex](../ide/codeindex-command.md) и флагом **\/indexHistoryPeriod**.  
  
 Чтобы просмотреть подробный журнал всех изменений, включая сделанные более года назад, выберите параметр **Показать все изменения файла**.  
  
 ![Показать все изменения кода](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  
  
 Откроется окно журнала с наборами изменений.  
  
 ![Окно журнала для всех изменений кода](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  
  
 Если ваши файлы хранятся в репозитории Git и вы выбираете индикатор изменений на уровне элемента кода, отображается следующее:  
  
 ![CodeLens: получение журнала изменений для кода в Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  
  
 Просмотрите изменения для всего файла \(кроме файлов C\# и Visual Basic\) на индикаторах уровня файла в нижней части окна.  
  
 ![CodeLens: получение сведений о файле кода](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  
  
 Чтобы получить дополнительные сведения об изменении, щелкните этот элемент правой кнопкой мыши. В зависимости от того, используется TFVC или Git, вам будут предложены варианты сравнения версий файла, просмотра сведений и отслеживания изменений, получения выбранной версии файла и уведомления автора об изменениях по электронной почте. Некоторые из этих сведений отображаются в Team Explorer.  
  
 Также можно узнать, кто вносил изменения в код в течение определенного времени. Это поможет обнаружить закономерности во вносимых рабочей группой изменениях и оценить их влияние.  
  
 ![CodeLens: просмотр журнала изменений кода в виде графа](../ide/media/codelens.png "CodeLens")  
  
#### Поиск изменений в текущем подразделении  
 Предположим, что ваша группа работает в нескольких подразделениях, основном и дочернем, для снижения риска нарушения стабильности кода:  
  
 ![CodeLens: узнайте, когда ваш код был разветвлен](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  
  
 Узнайте, сколько пользователей вносили изменения в код и сколько изменений было сделано в основном подразделении \(**ALT \+ 6**\):  
  
 ![CodeLens: узнайте, сколько изменений в вашей ветви](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  
  
#### Поиск разветвления кода  
 Перейдите к коду в дочернем подразделении, например Dev, как в этом примере. Выберите индикатор изменений \(**ALT \+ 6**\):  
  
 ![CodeLens: узнайте, когда ваш код был разветвлен](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  
  
#### Поиск входящих изменений от других подразделений  
 ![CodeLens: поиск изменений кода в других ветвях](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  
  
 …как это исправление ошибки в подразделении Dev:  
  
 ![CodeLens: изменение, зарегистрированное в другой ветви](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  
  
 Вы можете просмотреть это изменение, не покидая текущее подразделение \(Main\):  
  
 ![CodeLens: просмотр изменения, поступившего от другой ветви](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  
  
#### Поиск объединения изменений  
 Вы можете увидеть, какие изменения были добавлены в ваше подразделение:  
  
 ![CodeLens: слияние изменений между ветвями](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  
  
 Например, код в подразделении Main теперь содержит исправление ошибки из подразделения Dev:  
  
 ![CodeLens: слияние изменений между ветвями](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  
  
#### Сравните входящее изменение с локальной версией \(SHIFT \+ F10\).  
 ![CodeLens: сравнение поступившего изменения с локальным](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  
  
 Можно также дважды щелкнуть набор изменений.  
  
#### Что означают значки?  
  
|**Значок**|**Откуда поступило изменение?**|  
|----------------|-------------------------------------|  
|![CodeLens: значок "Изменение от текущей ветви"](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Текущее подразделение|  
|![CodeLens: значок "Изменение от родительской ветви"](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Родительское подразделение|  
|![CodeLens: значок "Изменение от дочерней ветви"](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Дочернее подразделение|  
|![CodeLens: значок "Изменение от одноранговой ветви"](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Одноранговое подразделение|  
|![CodeLens: значок "Изменение от дальней ветви"](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Подразделение, отличное от родительского, дочернего или однорангового|  
|![CodeLens: значок "Слияние от родительской ветви"](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Слияние с данными от родительского подразделения с дочерним подразделением|  
|![CodeLens: значок "Слияние от дочерней ветви"](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Слияние с данными от дочернего подразделения с родительским подразделением|  
|![CodeLens: значок "Слияние от несвязанной ветви"](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Слияние с данными от несвязанного подразделения \(слияние без базовой версии\)|  
  
### Поиск связанных рабочих элементов  
 ![CodeLens &#45; поиск рабочих элементов для конкретного кода](../ide/media/codelensworkitems.png "CodeLensWorkItems")  
  
### Поиск связанных проверок кода  
 ![CodeLens &#45; просмотр запросов на проверку кода](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  
  
### Поиск связанных ошибок  
 ![CodeLens &#45; поиск ошибок, связанных с наборами изменений](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  
  
### Обращение к владельцу элемента  
 ![Обращение к владельцу элемента](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  
  
 Откройте контекстное меню элемента, чтобы увидеть параметры контакта. Если на компьютере установлено приложение Lync или Skype для бизнеса, отобразятся следующие параметры:  
  
 ![Параметры контакта для элемента](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  
  
##  <a name="FindRunUnitTests"></a> Поиск модульных тестов для кода  
 Узнайте больше об имеющихся модульных тестах для кода, не открывая обозреватель тестов. Требуется:  
  
-   Visual Studio Enterprise или Visual Studio Professional  
  
-   Код Visual C\# .NET или Visual Basic .NET  
  
-   [Проект модульного теста](../test/unit-test-your-code.md) с модульными тестами для кода приложения  
  
1.  Перейдите к коду приложения с модульными тестами.  
  
2.  Просмотрите тестовый охват для этого кода \(**ALT \+ 3**\).  
  
     ![CodeLens &#45; выбор индикатора состояния тестирования в редакторе кода](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3.  Если отображается значок предупреждения ![CodeLens &#45; предупреждение о том, что модульные тесты еще не запускались](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), выполните тесты.  
  
     ![CodeLens &#45; просмотр еще не запускавшихся модульных тестов](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4.  Чтобы просмотреть определение теста, откройте файл кода в редакторе, дважды щелкнув элемент теста в окне индикаторов CodeLens.  
  
     ![CodeLens &#45; переход к определению модульного теста](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5.  Просмотрите результаты теста. Выберите индикатор состояния теста \(![CodeLens &#45; значок непройденного модульного теста](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") или ![CodeLens &#45; значок пройденного модульного теста](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")\) или нажмите клавиши **ALT\+1**.  
  
     ![CodeLens&#45; просмотр результатов модульного теста](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6.  Чтобы увидеть, сколько пользователей изменяло данный тест, кто именно его изменял или сколько изменений было внесено в тест, [Поиск журнала кода и связанных элементов](#FindCodeHistory).  
  
##  <a name="QA"></a> Вопросы и ответы  
  
###  <a name="ChangeOrTurnOff"></a> Вопрос. Как включить и выключить CodeLens? Как выбрать отображаемые индикаторы?  
 **Ответ.** Включать и выключать можно все индикаторы, кроме индикатора ссылок. Откройте меню **Инструменты** и последовательно выберите пункты **Параметры**, **Текстовый редактор**, **Все языки**, **CodeLens**.  
  
 Если индикаторы включены, параметры CodeLens можно также открыть из индикаторов.  
  
 ![Включение или выключение индикаторов CodeLens](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Индикаторы CodeLens уровня файла включаются и отключаются с помощью значка шеврона в нижней части окна редактора.  
  
 ![Включение и выключение индикаторов на уровне файла](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
###  <a name="NoIndicators"></a> Вопрос. Где находится CodeLens?  
 **Ответ.** CodeLens отображается в коде Visual C\# .NET и Visual Basic .NET на уровне метода, класса, индексатора и свойства. Для всех других типов файлов CodeLens отображается на уровне файла.  
  
-   Включите CodeLens. Откройте меню **Инструменты** и последовательно выберите пункты **Параметры**, **Текстовый редактор**, **Все языки**, **CodeLens**.  
  
-   Если код хранится в TFS, с помощью [команды CodeIndex](../ide/codeindex-command.md) и [команды TFS Config](http://msdn.microsoft.com/ru-ru/94424190-3b6b-4f33-a6b6-5807f4225b62) убедитесь, что индексирование кода включено.  
  
-   Индикаторы, связанные с TFS, отображаются, только когда рабочие элементы связаны с кодом и имеются разрешения на открытие связанных рабочих элементов.[Убедитесь в наличии разрешений члена команды.](http://msdn.microsoft.com/ru-ru/f58805de-ba61-4d09-8f2d-d3ab9662ecfd)  
  
-   Индикаторы модульных тестов не отображаются, если в коде приложения отсутствуют модульные тесты. Индикаторы состояния теста отображаются автоматически в тестовых проектах. Если известно, что код приложения имеет модульные тесты, но индикаторы тестов не отображаются, попробуйте выполнить сборку решения \(**CTRL \+ SHIFT \+ B**\).  
  
### Вопрос: Почему я не вижу сведения рабочего элемента для фиксации?  
 **Ответ.** Это может происходить, когда CodeLens не может найти рабочие элементы в TFS. Проверьте, что вы подключены к командному проекту, который имеет эти рабочие элементы, и что имеются разрешения для просмотра этих рабочих элементов. Это также может произойти, если описание фиксации содержит неверные сведения об идентификаторах рабочих элементов в TFS.  
  
###  <a name="NoLync"></a> Вопрос. Почему не отображаются индикаторы Lync или Skype?  
 **Ответ.** Они не отображаются, если вы не вошли в службу Lync или Skype для бизнеса, не установили ни одну из них или используете неподдерживаемую конфигурацию. Однако вы по\-прежнему можете отправлять почту:  
  
 ![CodeLens &#45; обращение к владельцу набора изменений по почте](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  
  
 **Какие конфигурации Lync и Skype поддерживаются?**  
  
-   Skype для бизнеса \(32\- или 64\-разрядная версия\)  
  
-   Lync 2010 или более поздняя версия отдельно \(32\- или 64\-разрядная\), но не Lync Basic 2013 с Windows 8.1  
  
 CodeLens не поддерживает наличие нескольких установленных версий Lync или Skype. Они могут быть не локализованы для всех локализованных версий Visual Studio.  
  
### Вопрос. Как изменить шрифт и цвет CodeLens?  
 **О.** Последовательно щелкните **Сервис**, **Параметры**, **Среда**, **Шрифты и цвета**.  
  
 ![CodeLens &#45; изменение параметров шрифта и цвета](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  
  
 Для использования клавиатуры выполните следующие действия.  
  
1.  Нажмите клавиши **ALT \+ T \+ O**, чтобы открыть окно **Параметры**.  
  
2.  Нажмите клавишу **СТРЕЛКА ВВЕРХ** или **СТРЕЛКА ВНИЗ**, чтобы перейти к узлу **Среда**, а затем нажмите клавишу **СТРЕЛКА ВЛЕВО**, чтобы развернуть узел.  
  
3.  Нажмите клавишу **СТРЕЛКА ВНИЗ**, чтобы перейти к пункту **Шрифты и цвета**.  
  
4.  Нажмите клавишу **TAB**, чтобы перейти к списку **Параметры для**, после чего нажмите клавишу **СТРЕЛКА ВНИЗ**, чтобы выбрать **CodeLens**.  
  
### В. Можно ли переместить HUD\-элемент CodeLens?  
 **Ответ.** Да, щелкните ![Закрепление CodeLens в виде окна](../ide/media/codelensdockwindow.png "CodeLensDockWindow"), чтобы закрепить CodeLens как окно.  
  
 ![Закрепить окно индикаторов CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  
  
 ![Закрепленное окно ссылок CodeLens](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  
  
### В. Как обновить индикаторы?  
 **Ответ.** Это зависит от индикатора.  
  
-   **Ссылки**: этот индикатор обновляется автоматически при изменении кода. Если этот индикатор закреплен в отдельном окне, его можно обновить вручную здесь:  
  
     ![CodeLens &#45; закрепление в виде окна](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  
  
-   **Команда**: эти индикаторы можно обновить вручную здесь:  
  
     ![Обновление индикаторов CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  
  
-   **Тест**: [Поиск модульных тестов для кода](#FindRunUnitTests), чтобы обновить этот индикатор.  
  
###  <a name="LocalVersion"></a> Вопрос. Что такое "Локальная версия"?  
 **О.** Стрелка **Локальная версия** указывает на последний набор изменений в локальной версии этого файла. Если на сервере находятся более новые наборы изменений, они отображаются над или под стрелкой **Локальная версия** в зависимости от порядка сортировки наборов изменений.  
  
### Вопрос. Можно ли управлять тем, как CodeLens обрабатывает код для отображения журнала и связанных элементов?  
 **Ответ.** Да, если код находится в TFS, используйте [команду CodeIndex](../ide/codeindex-command.md) с [командой TFS Config](http://msdn.microsoft.com/ru-ru/94424190-3b6b-4f33-a6b6-5807f4225b62).