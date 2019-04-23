---
title: Поиск изменений кода и других журналов с помощью CodeLens | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aa18bed0ff4dfa24de114f0b15c109dfba777c56
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055240"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Поиск изменений кода и других журналов с помощью CodeLens
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Получайте дополнительные сведения о коде, не отрываясь от работы и не выходя из редактора. Находите ссылки на код, изменения кода, связанные ошибки, рабочие элементы, проверки кода и модульные тесты.  
  
> [!NOTE]
>  Средство CodeLens доступно только в выпусках Visual Studio Enterprise и Visual Studio Professional. Оно не доступно в выпуске Visual Studio Community.  
  
 Посмотрите, где и как отдельные части вашего кода используются в решении.  
  
 ![Индикаторы CodeLens в редакторе кода](../ide/media/codelensoverview.png "CodeLensOverview")  
  
 Сообщите рабочей группе об изменениях в коде, не выходя из редактора.  
  
 ![CodeLens: обращение к рабочей группе](../ide/media/codelensovervew2.png "CodeLensOvervew2")  
  
 Чтобы выбрать, какие индикаторы должны отображаться, включить или выключить средство CodeLens, последовательно выберите пункты **Инструменты**, **Параметры**, **Текстовый редактор**, **Все языки**, **CodeLens**.  
  
## <a name="FindReferences"></a> Поиск ссылок на код  
 Требуется:  
  
- Visual Studio Enterprise или Visual Studio Professional  
  
- Код Visual C# .NET или Visual Basic .NET  
  
  Выберите индикатор **ссылок** (**ALT + 2**). Если в результатах отображается **0 ссылок**, это значит, что ссылки из кода Visual C# или Visual Basic отсутствуют. Сюда не входят ссылки из других элементов, таких как XAML- и ASPX-файлы.  
  
  ![CodeLens: выбор индикатора ссылок](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  
  
  Чтобы просмотреть код ссылки, наведите указатель мыши на ссылку.  
  
  ![CodeLens: просмотр ссылки](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  
  
  Чтобы открыть файл, на который указывает ссылка, дважды щелкните эту ссылку.  
  
  Чтобы просмотреть отношения между этим кодом и его ссылками, [создайте карту кода](../modeling/map-dependencies-across-your-solutions.md) и выберите параметр **Показать все ссылки** в контекстном меню карты кода.  
  
  ![CodeLens: ссылки на карте кода](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  
  
## <a name="FindCodeHistory"></a> Поиск журнала кода и связанных элементов  
 Просмотрите журнал кода, чтобы узнать, что случилось. Можно также изучить изменения до их внедрения в ваш код, чтобы понять, как изменения в других ветвях могут повлиять на него.  
  
 Требуется:  
  
- Visual Studio Enterprise или Visual Studio Professional  
  
- Team Foundation Server 2013 или более поздней версии, Visual Studio Team Services или Git  
  
- [Lync 2010 или более поздней версии или Skype для бизнеса](http://technet.microsoft.com/lync)(для связи с коллегами, не выходя из редактора кода)  
  
  Для кода на Visual C# .NET или Visual Basic .NET, который хранится вместе с системой управления версиями Team Foundation (TFVC) или Git, сведения CodeLens предоставляются на уровнях класса и метода (индикаторы*уровня кода элемента* ). Если репозиторий Git находится в TfGit, можно также получить ссылки на рабочие элементы TFS.  
  
  ![Индикаторы кода уровня элемента кода](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  
  
  Для всех других типов файлов, которые можно открыть в редакторе Visual Studio, сведения о CodeLens по всему файлу приводятся в одном месте — в нижней части окна (индикаторы*уровня файла* ).  
  
  ![Индикаторы CodeLens уровня файла](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  
  
  Чтобы выбрать индикатор с помощью клавиатуры, нажмите и удерживайте клавишу **ALT** для отображения назначенных клавиш с цифрами.  
  
  ![Нажмите клавишу ALT для просмотра клавиш с цифрами](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  
  
### <a name="find-changes-in-your-code"></a>Поиск изменений в коде  
 Узнайте, кто изменил ваш код на C# или Visual Basic, и просмотрите внесенные в код изменения на индикаторах уровня кода элемента. При использовании системы управления версиями Team Foundation (TFVC) в Team Foundation Server или Visual Studio Team Services отображается следующее.  
  
 ![CodeLens: Получение журнала изменений для кода в TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  
  
 Период времени по умолчанию — последние 12 месяцев. Если код хранится в Team Foundation Server, это ограничение можно изменить, выполнив [команду TFSConfig](http://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) вместе с [командой CodeIndex](../ide/codeindex-command.md) и флагом **/indexHistoryPeriod** .  
  
 Чтобы просмотреть подробный журнал всех изменений, включая сделанные более года назад, выберите параметр **Показать все изменения файла**.  
  
 ![Показать все изменения кода](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  
  
 Откроется окно журнала с наборами изменений.  
  
 ![Окно журнала для всех изменений кода](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  
  
 Если ваши файлы хранятся в репозитории Git и вы выбираете индикатор изменений на уровне элемента кода, отображается следующее:  
  
 ![CodeLens: Получение журнала изменений для кода в Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  
  
 Просмотрите изменения для всего файла (кроме файлов C# и Visual Basic) на индикаторах уровня файла в нижней части окна.  
  
 ![CodeLens: Получение сведений о файле кода](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  
  
 Чтобы получить дополнительные сведения об изменении, щелкните этот элемент правой кнопкой мыши. В зависимости от того, используется TFVC или Git, вам будут предложены варианты сравнения версий файла, просмотра сведений и отслеживания изменений, получения выбранной версии файла и уведомления автора об изменениях по электронной почте. Некоторые из этих сведений отображаются в Team Explorer.  
  
 Также можно узнать, кто вносил изменения в код в течение определенного времени. Это поможет обнаружить закономерности во вносимых рабочей группой изменениях и оценить их влияние.  
  
 ![CodeLens: Просмотр журнала изменений кода в виде графа](../ide/media/codelens.png "CodeLens")  
  
#### <a name="find-changes-in-your-current-branch"></a>Поиск изменений в текущем подразделении  
 Предположим, что ваша группа работает в нескольких подразделениях, основном и дочернем, для снижения риска нарушения стабильности кода:  
  
 ![CodeLens: Узнайте, когда ваш код был разветвлен](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  
  
 Узнайте, сколько пользователей вносили изменения в код и сколько изменений было сделано в основном подразделении (**ALT + 6**):  
  
 ![CodeLens: Найти числа изменений в ветви](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  
  
#### <a name="find-when-your-code-was-branched"></a>Поиск разветвления кода  
 Перейдите к коду в дочернем подразделении, например Dev, как в этом примере. Выберите индикатор изменений (**ALT + 6**):  
  
 ![CodeLens: Узнайте, когда ваш код был разветвлен](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  
  
#### <a name="find-incoming-changes-from-other-branches"></a>Поиск входящих изменений от других подразделений  
 ![CodeLens: Поиск изменений кода в других ветвях](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  
  
 …как это исправление ошибки в подразделении Dev:  
  
 ![CodeLens: Изменение, зарегистрированное в другой ветви](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  
  
 Вы можете просмотреть это изменение, не покидая текущее подразделение (Main):  
  
 ![CodeLens: Просмотр изменения, поступившего от другой ветви](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  
  
#### <a name="find-when-changes-got-merged"></a>Поиск объединения изменений  
 Вы можете увидеть, какие изменения были добавлены в ваше подразделение:  
  
 ![CodeLens: объединение изменений между ветвями](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  
  
 Например, код в подразделении Main теперь содержит исправление ошибки из подразделения Dev:  
  
 ![CodeLens: объединение изменений между ветвями](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  
  
#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Сравните входящее изменение с локальной версией (SHIFT + F10).  
 ![CodeLens: Сравнение поступившего изменения с локальным](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  
  
 Можно также дважды щелкнуть набор изменений.  
  
#### <a name="what-do-the-icons-mean"></a>Что означают значки?  
  
|**Значок**|**Откуда поступило изменение?**|  
|--------------|-----------------------------------------|  
|![CodeLens: Изменение от текущей ветви значок](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Текущее подразделение|  
|![CodeLens: значок "Изменение от родительской ветви"](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Родительское подразделение|  
|![CodeLens: Изменить значок ветви дочерних](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Дочернее подразделение|  
|![CodeLens: значок "Изменение от одноранговой ветви"](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Одноранговое подразделение|  
|![CodeLens: значок "Изменение от другой ветви"](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Подразделение, отличное от родительского, дочернего или однорангового|  
|![CodeLens: Слияние от родительской значок](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Слияние с данными от родительского подразделения с дочерним подразделением|  
|![CodeLens: Слияние от ветви значок дочерних](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Слияние с данными от дочернего подразделения с родительским подразделением|  
|![CodeLens: Слияние от несвязанной ветви значок](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Слияние с данными от несвязанного подразделения (слияние без базовой версии)|  
  
### <a name="find-linked-work-items"></a>Поиск связанных рабочих элементов  
 ![CodeLens: поиск рабочих элементов для конкретного кода](../ide/media/codelensworkitems.png "CodeLensWorkItems")  
  
### <a name="find-linked-code-reviews"></a>Поиск связанных проверок кода  
 ![CodeLens: просмотр запросов на проверку кода](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  
  
### <a name="find-linked-bugs"></a>Поиск связанных ошибок  
 ![CodeLens: поиск ошибок, связанных с наборами изменений](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  
  
### <a name="contact-the-owner-of-an-item"></a>Обращение к владельцу элемента  
 ![Обращение к владельцу элемента](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  
  
 Откройте контекстное меню элемента, чтобы увидеть параметры контакта. Если на компьютере установлено приложение Lync или Skype для бизнеса, отобразятся следующие параметры:  
  
 ![Параметры контакта для элемента](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  
  
## <a name="FindRunUnitTests"></a> Поиск модульных тестов для кода  
 Узнайте больше об имеющихся модульных тестах для кода, не открывая обозреватель тестов. Требуется:  
  
- Visual Studio Enterprise или Visual Studio Professional  
  
- Код Visual C# .NET или Visual Basic .NET  
  
- [Проект модульного теста](../test/unit-test-your-code.md) с модульными тестами для кода приложения  
  
1. Перейдите к коду приложения с модульными тестами.  
  
2. Просмотрите тестовый охват для этого кода (**ALT + 3**).  
  
     ![CodeLens: выбор состояния тестирования в редакторе кода](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3. Если отображается значок предупреждения ![CodeLens: предупреждение о том, что модульные тесты еще не запускались](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), выполните тесты.  
  
     ![CodeLens: просмотр еще не запускавшихся модульных тестов](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4. Чтобы просмотреть определение теста, откройте файл кода в редакторе, дважды щелкнув элемент теста в окне индикаторов CodeLens.  
  
     ![CodeLens: переход к определению модульного теста](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5. Просмотрите результаты теста. Выберите индикатор состояния теста (![CodeLens: значок непройденного модульного теста](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") или ![CodeLens: значок пройденного модульного теста](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")) или нажмите сочетание клавиш **ALT+1**.  
  
     ![CodeLens: просмотр результат модульного теста](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6. Чтобы увидеть, сколько пользователей изменяло данный тест, кто именно изменял тест или сколько изменений было внесено в тест, [Поиск журнала кода и связанных элементов](#FindCodeHistory).  
  
## <a name="QA"></a> Вопросы и ответы  
  
### <a name="ChangeOrTurnOff"></a> Вопрос. Как отключить CodeLens, или включить? Как выбрать отображаемые индикаторы?  
 **Ответ.**  Включать и выключать можно все индикаторы, кроме индикатора ссылок. Откройте меню **Инструменты**и последовательно выберите пункты **Параметры**, **Текстовый редактор**, **Все языки**, **CodeLens**.  
  
 Если индикаторы включены, параметры CodeLens можно также открыть из индикаторов.  
  
 ![CodeLens: включение или отключение индикаторов](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Индикаторы CodeLens уровня файла включаются и отключаются с помощью значка шеврона в нижней части окна редактора.  
  
 ![Включение и отключение индикаторов уровня файла](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
### <a name="NoIndicators"></a> Вопрос. Где находится CodeLens?  
 **Ответ.** CodeLens отображается в визуальном C# коде .NET и Visual Basic .NET на уровне метода, класса, индексатора и свойства. Для всех других типов файлов CodeLens отображается на уровне файла.  
  
- Включите CodeLens. Откройте меню **Инструменты**и последовательно выберите пункты **Параметры**, **Текстовый редактор**, **Все языки**, **CodeLens**.  
  
- Если код хранится в TFS, с помощью [команды CodeIndex](../ide/codeindex-command.md) и [команды TFS Config](http://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)убедитесь, что индексирование кода включено.  
  
- Индикаторы, связанные с TFS, отображаются, только когда рабочие элементы связаны с кодом и имеются разрешения на открытие связанных рабочих элементов. [Убедитесь в наличии разрешений члена команды.](/azure/devops/organizations/security/view-permissions)  
  
- Индикаторы модульных тестов не отображаются, если в коде приложения отсутствуют модульные тесты. Индикаторы состояния теста отображаются автоматически в тестовых проектах. Если известно, что код приложения имеет модульные тесты, но индикаторы тестов не отображаются, попробуйте выполнить сборку решения (**CTRL + SHIFT + B**).  
  
### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Вопрос: Почему я не вижу сведения рабочего элемента для фиксации?  
 **Ответ.** Это может произойти, когда CodeLens не может найти рабочие элементы в TFS. Проверьте, что вы подключены к командному проекту, который имеет эти рабочие элементы, и что имеются разрешения для просмотра этих рабочих элементов. Это также может произойти, если описание фиксации содержит неверные сведения об идентификаторах рабочих элементов в TFS.  
  
### <a name="NoLync"></a> Вопрос. Почему не отображаются индикаторы Lync или Скайп?  
 **Ответ.** Они не отображаются, если вы не вошли в Lync или Скайп для бизнеса, нет ни одного из них или не является поддерживаемой конфигурацией. Однако вы по-прежнему можете отправлять почту:  
  
 ![CodeLens: обращение к владельцу набора изменений по почте](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  
  
 **Какие конфигурации Lync и Skype поддерживаются?**  
  
- Skype для бизнеса (32- или 64-разрядная версия)  
  
- Lync 2010 или более поздняя версия отдельно (32- или 64-разрядная), но не Lync Basic 2013 с Windows 8.1  
  
  CodeLens не поддерживает наличие нескольких установленных версий Lync или Skype. Они могут быть не локализованы для всех локализованных версий Visual Studio.  
  
### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Вопрос: Как изменить шрифт и цвет CodeLens?  
 **Ответ.** Перейдите к **средства**, **параметры**, **среды**, **шрифты и цвета**.  
  
 ![CodeLens: изменение параметров шрифта и цвета](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  
  
 Для использования клавиатуры выполните следующие действия.  
  
1. Нажмите клавиши **ALT + T + O** , чтобы открыть окно **Параметры** .  
  
2. Нажмите клавишу **СТРЕЛКА ВВЕРХ** или **СТРЕЛКА ВНИЗ** , чтобы перейти к узлу **Среда** , а затем нажмите клавишу **СТРЕЛКА ВЛЕВО** , чтобы развернуть узел.  
  
3. Нажмите клавишу **СТРЕЛКА ВНИЗ** , чтобы перейти к пункту **Шрифты и цвета**.  
  
4. Нажмите клавишу **TAB** , чтобы перейти к списку **Параметры для** , после чего нажмите клавишу **СТРЕЛКА ВНИЗ** , чтобы выбрать **CodeLens**.  
  
### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Вопрос: Можно ли переместить HUD-элемент CodeLens?  
 **Ответ.** Да, выберите ![CodeLens &#45; Закрепить как окно](../ide/media/codelensdockwindow.png "CodeLensDockWindow") , чтобы закрепить CodeLens как окно.  
  
 ![Закрепить окно индикаторов CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  
  
 ![Закрепленное окно ссылок CodeLens](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  
  
### <a name="q-how-do-i-refresh-the-indicators"></a>Вопрос: Как обновить индикаторы?  
 **Ответ.** Это зависит от индикатора.  
  
- **Ссылки**: этот индикатор обновляется автоматически при изменении кода. Если этот индикатор закреплен в отдельном окне, его можно обновить вручную здесь:  
  
     ![CodeLens: закрепление в виде окна](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  
  
- **Команда**: Эти индикаторы можно обновите вручную здесь:  
  
     ![CodeLens: обновление индикаторов](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  
  
- **Тест**: [Поиск модульных тестов для кода](#FindRunUnitTests) чтобы обновить тот индикатор.  
  
### <a name="LocalVersion"></a> Вопрос. Что такое "Локальная версия"?  
 **Ответ.** **Локальная версия** стрелка указывает на последний набор изменений в локальной версии этого файла. Если на сервере находятся более новые наборы изменений, они отображаются над или под стрелкой **Локальная версия** в зависимости от порядка сортировки наборов изменений.  
  
### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Вопрос: Можно ли управлять тем, как CodeLens обрабатывает код для отображения журнала и связанных элементов?  
 **Ответ.** Да, если код находится в TFS, используйте [команда CodeIndex](../ide/codeindex-command.md) с [командой TFS Config](http://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).
