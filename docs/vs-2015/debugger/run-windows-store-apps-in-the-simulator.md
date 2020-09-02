---
title: Запуск приложений Магазина Windows в симуляторе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d072f54dfe351d54e3e115dca7a91bec77fbb9e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844932"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Запуск приложений для Магазина Windows в симуляторе
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Симулятор Visual Studio для приложений для Магазина Windows является приложением рабочего стола, которое имитирует приложение для Магазина Windows. Вы можете запускать приложения и имитировать общие события касания и поворота экрана на компьютере разработки. Вы также можете выбирать физический размер и разрешение экрана, которые требуется моделировать, и имитировать свойства сетевых подключений.  
  
 Имитатор предоставляет среду, в которой можно проектировать, разрабатывать, отлаживать и тестировать приложения для Магазина Windows. Однако прежде чем публиковать приложение в Магазине Windows, его необходимо протестировать на настоящем устройстве.  
  
 Симулятор Visual Studio для приложений для Магазина Windows не выполняется в изолированной среде на локальном компьютере. Поэтому ошибки, возникающие в симуляторе, например неустранимая системная ошибка, могут также влиять на весь компьютер.  
  
 Сведения о Windows Phone см. в разделе [Run Windows Phone apps in the emulator](../debugger/run-windows-phone-apps-in-the-emulator.md) .  
  
> [!IMPORTANT]
> Имитатор Visual Studio 2015 не включает кнопку географического положения. Это вызвано тем, что в имитаторе Windows 10 не предусмотрено моделирование географического положения. Если требуется выполнить моделирование такого рода, можно использовать имитатор Visual Studio 2013 для Windows 8.1 или более ранних операционных систем.  
  
## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a> Установка симулятора в качестве целевого объекта  
 Чтобы запустить приложение для Магазина Windows в симуляторе, выберите **Симулятор** из раскрывающегося списка рядом с кнопкой **Начать отладку** на панели инструментов **Стандартная** отладчика.  
  
 ![Запуск в симуляторе](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a> Выбор режима взаимодействия  
 Вы можете выбрать следующие режимы взаимодействия.  
  
- ![Кнопка режима мыши.](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") Режим мыши устанавливает режим взаимодействия с помощью жестов мыши. К жестам мыши относятся щелчки, двойные щелчки и перетаскивания.  
  
- ![Кнопка эмуляции сенсорного экрана.](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Эмуляция сенсорного экрана: устанавливает режим взаимодействия с помощью жестов касания одним пальцем. К события касания одним пальцем относятся касания, перетаскивания и проведение пальцем по экрану.  
  
     ![Цель одного пальца имитатора](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") Значок одного целевого объекта указывает расположение событий в симуляторе. Используйте мышь для перемещения указателя.  
  
     ![Один целевой объект сенсорного пальца](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") Нажмите левую кнопку мыши, чтобы активировать сенсорный режим. Например, нажмите кнопку, чтобы сымитировать касание, или нажмите и удерживайте кнопку по мере перетаскивания или проведения.  
  
## <a name="pinch-and-zoom"></a>Жест сжатия и масштабирования  
 Устанавливает режим взаимодействия с помощью жестов сжатия и масштабирования, выполняемых двумя пальцами.  
  
- ![Цель для двух пальцев в симуляторе](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  

  - Двойной целевой значок указывает расположение двух пальцев на экране устройства.  

  - Переместите указатель мыши, чтобы расположить значки над объектом на экране устройства.  

  - Поворачивайте колесико мыши назад или вперед, чтобы изменить сымитированное расстояние между двумя пальцами до сжатия или масштабирования.  

- ![Сжатие, увеличение и поворот целевых объектов](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  

  - Нажмите левую кнопку и поворачивайте колесико мыши назад (к себе), чтобы увеличить масштаб (сжатие).  

  - Нажмите левую кнопку и поворачивайте колесико мыши вперед (от себя), чтобы уменьшить масштаб (масштабирование).  
  
## <a name="object-rotation"></a>Поворот объекта  
 Кнопка **Эмуляция сенсорного экрана: вращение** устанавливает режим взаимодействия с помощью жестов поворота, выполняемых двумя пальцами.  
  
- Переместите указатель мыши, чтобы расположить значки над объектом на экране устройства.  
  
  - Поворачивайте колесико мыши назад или вперед, чтобы изменить сымитированную ориентацию двух пальцев до поворота объекта.  

- Нажмите левую кнопку и поворачивайте колесико мыши назад (к себе), чтобы повернуть объект против часовой стрелки. По мере поворота колесика мыши один из двух целевых значков вращается вокруг другого для указания относительного размера поворота.  

  - Нажмите левую кнопку и поворачивайте колесико мыши вперед (от себя), чтобы повернуть объект по часовой стрелке.  

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Включение или отключение режима "Поверх остальных окон"  
 Можно указать, чтобы окно симулятора всегда отображалось поверх других окон. Кнопка **Переключение на самое верхнее окно** включает или отключает режим **Поверх остальных окон** для окна имитатора.  
  
## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a> Изменение ориентации устройства  
 Можно переключиться между книжной и альбомной ориентацией устройства, повернув симулятор на 90 градусов в любом направлении.  
  
> [!NOTE]
> Имитатор не связан со свойством [DisplayProperties.AutoRotationPreferences](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayproperties.autorotationpreferences.aspx) проекта. Например, если для проекта задать ориентацию `Landscape`, а затем повернуть симулятор для отображения в книжной ориентации, изображение симулятора также будет повернуто, и его размер будет изменен. Проверьте эти параметры на настоящем устройстве.  
  
> [!NOTE]
> При повороте симулятора таким образом, что один его край больше экрана, на котором он отображается, размер симулятора изменяется автоматически для соответствия размеру экрана. Размер симулятора не изменяется до исходного при повторном повороте симулятора.  
  
## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Изменение размера и разрешения сымитированного экрана  
 Чтобы изменить размер и разрешение смоделированного экрана, нажмите кнопку **Изменить разрешение** в палитре и выберите новый размер и разрешение из списка.  
  
 Размер и разрешение экрана указываются в виде *Ширина экрана в дюймах, ширина в пикселях X высота в пикселях*. Обратите внимание на то, что имитируется и размер, и разрешение экрана. Координаты расположения в симуляторе преобразуются в координаты выбранного размера и разрешения устройства.  
  
> [!NOTE]
> Можно сохранить масштабированные версии точечных рисунков в приложении, и Windows загрузит правильный рисунок для текущего масштаба. Дополнительные сведения см. в разделе [Адаптивное проектирование 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Однако, если изменить разрешение симулятора таким образом, чтобы ОС Windows выбрала другое изображение для соответствия разрешению, необходимо остановить и перезапустить сеанс отладки для просмотра нового изображения.  
  
## <a name="capture-a-screenshot-of-your-app-for-submission-to-the-windows-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Создание снимка приложения для представления в Магазин Windows  
 При отправке приложения в Магазин Windows необходимо включить его снимки экрана.  
  
> [!NOTE]
> Снимок экрана сохраняется в текущем разрешении симулятора. Чтобы изменить разрешение, нажмите кнопку **Изменить разрешение** .  
  
- Для создания снимков экрана приложения в симуляторе нажмите кнопку **Запись снимка экрана в буфер обмена** .  
  
- Чтобы задать расположение снимков экрана, нажмите кнопку **Параметры снимка экрана** и выберите расположение из контекстного меню.  
  
     ![Контекстное меню параметров снимка экрана](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a> Имитация свойств сетевых подключений  
 Можно помочь пользователям приложения управлять расходами на оплату сетевых подключений с лимитным тарифным планом путем уведомления о стоимости сетевых подключений или изменениях состояния тарифных планов и предоставления приложению возможности использовать эти сведения, чтобы избежать дополнительных расходов на оплату роуминга или затрат из-за превышения заданного ограничения на передачу данных. Интерфейсы API [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) позволяют реагировать на события [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) и [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) , на которые имеется подписка. Подробнее см. в [кратком руководстве по управлению ограничениями расходов на оплату сетевых подключений с лимитным тарифным планом](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Для отладки или тестирования кода, поддерживающего стоимость сети, симулятор может имитировать свойства сети, предоставляемые через объект [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) , возвращенный [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx).  
  
 Для имитации свойств сети выполните следующие действия.  
  
1. В панели инструментов имитатора нажмите кнопку **Изменение свойств сети** .  
  
2. В диалоговом окне **Установка свойств сети** установите флажок **Использовать имитированные свойства сети**.  
  
    Снимите флажок, чтобы удалить имитацию и вернуться к свойствам сети подключенного в данный момент интерфейса.  
  
3. Введите **Имя профиля** для сымитированной сети. Рекомендуется ввести уникальное имя, которое можно использовать для идентификации имитации в свойстве [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) объекта [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) .  
  
4. Выберите для профиля значение [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) из списка **Тип стоимости сети** .  
  
5. Из списка **Флаг состояния лимита данных** можно задать для свойства [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) или [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)значение true или выбрать **Лимит данных не достигнут** , чтобы установить для обоих свойств значение false.  
  
6. Из списка **Состояние роуминга** установите свойство [Roaming](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) .  
  
7. Выберите **Задать свойства** для имитации свойств сети путем активации события [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) переднего плана и фонового триггера [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) типа **NetworkStateChange**.  
  
   **Дополнительные сведения об управлении сетевыми подключениями**  
  
   [Краткое руководство. Управление ограничениями расходов на оплату сетевых подключений с лимитным тарифным планом](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
   [Пример информации по сети](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Анализ энергопотребления](../profiling/analyze-energy-use-in-store-apps.md)  
    
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Реакция на системные события с фоновыми задачами](https://msdn.microsoft.com/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Вызов событий приостановки, возобновления и фоновых событий в приложениях для Магазина Windows](https://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Навигация по симулятору с помощью клавиатуры  
 Вы можете перейти в панель инструментов имитатора, нажав сочетание клавиш **CTRL+ALT+стрелка вверх** , чтобы перенести фокус с окна имитатора в панель инструментов имитатора. Используйте клавиши **Стрелка вверх** и **Стрелка вниз** для перемещения между кнопками панели инструментов.  
  
 Чтобы завершить работу имитатора, нажмите сочетание клавиш **CTRL+ALT+F4**.  
  
## <a name="see-also"></a>См. также:  
 [Запуск приложения из Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
