---
title: Запуск приложений UWP в симуляторе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: b7d68a23ffba12e9654ac047629bd64ecfae4bb6
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661906"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Запуск приложений UWP в симуляторе

Симулятор Visual Studio для приложений UWP — это классическое приложение, моделирующее приложение UWP. Как правило, отладка будет выполняться на локальном компьютере, подключенном устройстве или на удаленном компьютере. Однако в некоторых случаях может потребоваться использовать симулятор Visual Studio для имитации различных физических размеров экрана и разрешения. Можно также имитировать общие события сенсорного ввода и вращения и имитировать свойства сетевого подключения.

Симулятор предоставляет среду, в которой можно проектировать, разрабатывать, отлаживать и тестировать приложения UWP. Однако перед публикацией приложения на Microsoft Store необходимо протестировать приложение на фактическом устройстве.

Симулятор Visual Studio для приложений UWP не выполняется в изолированной среде на локальном компьютере. Поэтому ошибки, возникающие в симуляторе, например неустранимая системная ошибка, могут также влиять на весь компьютер.

> [!IMPORTANT]
> Имитатор Visual Studio 2015 не включает кнопку географического положения. Это вызвано тем, что в имитаторе Windows 10 не предусмотрено моделирование географического положения.

## <a name="BKMK_Set_the_simulator_as_the_target"></a> Установка симулятора в качестве целевого объекта

Чтобы запустить приложение UWP в симуляторе, выберите **симулятор** из раскрывающегося списка рядом с кнопкой **начать отладку** на **стандартной** панели инструментов отладчика. Этот параметр доступен только в том случае, если **Минимальная версия целевой платформы** приложения меньше или равна операционной системе на компьютере разработки.

![Запуск в симуляторе](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="BKMK_Choose_an_interaction_mode"></a> Выбор режима взаимодействия

Можно выбрать следующие режимы взаимодействия:

- ![Кнопка режима мыши](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Режим мыши: устанавливает режим взаимодействия для жестов мыши. К жестам мыши относятся щелчки, двойные щелчки и перетаскивания.

- ![Кнопка запуска эмуляции сенсорного экрана](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Запустить эмуляцию сенсорного ввода: задает режим взаимодействия для сенсорных жестов одного пальца. К события касания одним пальцем относятся касания, перетаскивания и проведение пальцем по экрану.

   ![Цель одного пальца имитатора](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   Один целевой значок указывает расположение событий в имитаторе. Используйте мышь для перемещения указателя.

   ![Один целевой объект сенсорного пальца](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Нажмите левую кнопку мыши, чтобы активировать сенсорный режим. Например, нажмите кнопку, чтобы сымитировать касание, или нажмите и удерживайте кнопку по мере перетаскивания или проведения.

## <a name="pinch-and-zoom"></a>Жест сжатия и масштабирования

Устанавливает режим взаимодействия с помощью жестов сжатия и масштабирования, выполняемых двумя пальцами.

![Цель двустороннего пальца имитатора](../debugger/media/simulator_twofinger.png)

Двойной целевой значок указывает расположение двух пальцев на экране устройства.

- Переместите указатель мыши, чтобы расположить значки над объектом на экране устройства.

- Поворачивайте колесико мыши назад или вперед, чтобы изменить сымитированное расстояние между двумя пальцами до сжатия или масштабирования.

![Сжатие, увеличение и поворот целевых объектов](../debugger/media/simulator_twofingerengaged.png)

- Нажмите левую кнопку и поворачивайте колесико мыши назад (к себе), чтобы увеличить масштаб (сжатие).

- Нажмите левую кнопку и поворачивайте колесико мыши вперед (от себя), чтобы уменьшить масштаб (масштабирование).

## <a name="object-rotation"></a>Поворот объекта

Кнопка **Эмуляция сенсорного экрана: вращение** устанавливает режим взаимодействия с помощью жестов поворота, выполняемых двумя пальцами.

- Переместите указатель мыши, чтобы расположить значки над объектом на экране устройства. Поворачивайте колесико мыши назад или вперед, чтобы изменить сымитированную ориентацию двух пальцев до поворота объекта.

- Нажмите левую кнопку и поворачивайте колесико мыши назад (к себе), чтобы повернуть объект против часовой стрелки. По мере поворота колесика мыши один из двух целевых значков вращается вокруг другого для указания относительного размера поворота.

- Нажмите левую кнопку и поворачивайте колесико мыши вперед (от себя), чтобы повернуть объект по часовой стрелке.

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Включение или отключение режима "Поверх остальных окон"
 Можно указать, чтобы окно симулятора всегда отображалось поверх других окон. Кнопка **Переключение на самое верхнее окно** включает или отключает режим **Поверх остальных окон** для окна имитатора.

## <a name="BKMK_Change_the_device_orientation"></a> Изменение ориентации устройства
 Можно переключиться между книжной и альбомной ориентацией устройства, повернув симулятор на 90 градусов в любом направлении.

> [!NOTE]
> Имитатор не связан со свойством [DisplayProperties.AutoRotationPreferences](/uwp/api/windows.graphics.display.displayproperties.autorotationpreferences) проекта. Например, если для проекта задать ориентацию `Landscape`, а затем повернуть симулятор для отображения в книжной ориентации, изображение симулятора также будет повернуто, и его размер будет изменен. Проверьте эти параметры на настоящем устройстве.

> [!NOTE]
> При повороте симулятора таким образом, что один его край больше экрана, на котором он отображается, размер симулятора изменяется автоматически для соответствия размеру экрана. Размер симулятора не изменяется до исходного при повторном повороте симулятора.

## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Изменение размера и разрешения сымитированного экрана
 Чтобы изменить размер и разрешение смоделированного экрана, нажмите кнопку **Изменить разрешение** в палитре и выберите новый размер и разрешение из списка.

 Размер и разрешение экрана указываются в виде *Ширина экрана в дюймах, ширина в пикселях X высота в пикселях*. Обратите внимание на то, что имитируется и размер, и разрешение экрана. Координаты местоположения в симуляторе преобразуются в выбранный размер и разрешение устройства.

> [!NOTE]
> Можно сохранить масштабированные версии точечных рисунков в приложении, и Windows загрузит правильный рисунок для текущего масштаба. Дополнительные сведения см. в разделе [Разработка и введение в пользовательский интерфейс](/windows/uwp/layout/design-and-ui-intro). Однако, если изменить разрешение симулятора таким образом, чтобы ОС Windows выбрала другое изображение для соответствия разрешению, необходимо остановить и перезапустить сеанс отладки для просмотра нового изображения.

## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Запись снимка экрана приложения для отправки в Microsoft Store
 При отправке приложения в Microsoft Store необходимо включить снимки экрана приложения.

> [!NOTE]
> Снимок экрана сохраняется в текущем разрешении симулятора. Чтобы изменить разрешение, нажмите кнопку **Изменить разрешение** .

- Для создания снимков экрана приложения в симуляторе нажмите кнопку **Запись снимка экрана в буфер обмена** .

- Чтобы задать расположение снимков экрана, нажмите кнопку **Параметры снимка экрана** и выберите расположение из контекстного меню.

   ![Контекстное меню параметров снимка экрана](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="BKMK_Simulate_network_connection_properties"></a> Имитация свойств сетевых подключений

Можно помочь пользователям приложения управлять расходами на оплату сетевых подключений с лимитным тарифным планом путем уведомления о стоимости сетевых подключений или изменениях состояния тарифных планов и предоставления приложению возможности использовать эти сведения, чтобы избежать дополнительных расходов на оплату роуминга или затрат из-за превышения заданного ограничения на передачу данных. Интерфейсы API [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) позволяют реагировать на события [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) и [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) , на которые имеется подписка. См. [краткое руководство по управлению ограничениями расходов на оплату сетевых подключений с лимитным тарифным планом](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).

Чтобы выполнить отладку или тестирование кода, учитывающего стоимость сетевых подключений, имитатор может имитировать свойства сети, представляемые с помощью объекта [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile), который возвращается методом [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).

Для имитации свойств сети выполните следующие действия.

1. В панели инструментов имитатора нажмите кнопку **Изменение свойств сети** .

2. В диалоговом окне **Установка свойств сети** установите флажок **Использовать имитированные свойства сети**.

    Снимите флажок, чтобы удалить имитацию и вернуться к свойствам сети подключенного в данный момент интерфейса.

3. Введите **Имя профиля** для сымитированной сети. Рекомендуется ввести уникальное имя, которое можно использовать для идентификации имитации в свойстве [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) объекта [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) .

4. Выберите для профиля значение [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) из списка **Тип стоимости сети** .

5. Из списка **Флаг состояния лимита данных** можно задать для свойства [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) или [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) значение true или выбрать **Лимит данных не достигнут**, чтобы установить для обоих свойств значение false.

6. Из списка **Состояние роуминга** установите свойство [Roaming](/uwp/api/windows.networking.connectivity.connectioncost) .

7. Выберите **Задать свойства** для имитации свойств сети путем активации события [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) переднего плана и фонового триггера [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) типа **NetworkStateChange**.

Дополнительные сведения об управлении сетевыми подключениями см. в следующих статьях:

[краткое руководство по управлению ограничениями расходов на оплату сетевых подключений с лимитным тарифным планом](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)

[Пример информации по сети](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[Анализ энергопотребления](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)

[Реакция на системные события с фоновыми задачами](/previous-versions/windows/apps/hh977058(v=win.10))

[Вызов событий приостановки, возобновления и фоновых событий в приложениях UWP](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Навигация по симулятору с помощью клавиатуры

Можно перейти на панель инструментов имитатора, нажав клавиши **CTRL + ALT + стрелка вверх** , чтобы переключить фокус с окна симулятора на панель инструментов имитатора. Используйте клавиши **Стрелка вверх** и **Стрелка вниз** для перемещения между кнопками панели инструментов.

Вы можете завершить работу симулятора, нажав клавиши **CTRL + ALT + F4**.

## <a name="see-also"></a>См. также

- [Запуск приложения из Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
