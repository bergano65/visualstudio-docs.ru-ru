---
title: 'Практическое: использование диагностики графики с устройством ARM | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24067412f875001185a0709c41f930ce3cdc8f3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568755"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Практическое руководство. Использование диагностики графики с устройством ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: использование диагностики графики с устройством ARM](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-use-graphics-diagnostics-with-an-arm-device).  
  
Диагностика графики поддерживает удаленную отладку приложений Direct3D на устройствах с архитектурой ARM с ОС Windows RT 8.1 или Windows Phone 8.1. Вы можете захватывать графические данные из приложения Direct3D, выполняющегося на устройстве, или использовать устройство в качестве компьютера воспроизведения для ранее захваченных графических данных.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Использование диагностики графики с устройством на основе ARM  
 Так как Visual Studio не запускается на устройствах с архитектурой ARM, для анализа приложения, выполняющегося на таком устройстве, необходимо использовать удаленный отладчик. Удаленный отладчик поддерживает захват и воспроизведение графики, что позволяет диагностировать ошибки отрисовки и оценивать производительность обработки графики на таких устройствах так же легко, как выполнять отладку приложений на них.  
  
 Для использования возможностей диагностики графики сначала включите на устройстве удаленную отладку.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Включение удаленной отладки на устройстве с архитектурой ARM  
  
1.  Установка [политику комплектов ARM](http://msdn.microsoft.com/windows/desktop/dn469188) на устройстве на основе ARM.  
  
2.  Установка [инструменты удаленной отладки](http://go.microsoft.com/fwlink/?LinkId=393086) на устройстве на основе ARM.  
  
> [!IMPORTANT]
>  В случае с устройствами Windows Phone 8.1 необходимо зарегистрировать телефон для разработки. Для этого вы должны быть зарегистрированным разработчиком. Дополнительные сведения см. в разделе [как развернуть и запустить приложение для Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Включив удаленную отладку на устройстве, сделайте его целевым объектом отладки и запустите диагностику графики.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Настройка и запуск диагностики графики на устройстве  
  
1.  На **платформ решения** стрелку раскрывающегося списка выберите **ARM** таким образом, чтобы устройства на базе ARM будут доступны как цели удаленной отладки.  
  
2.  На **целевой объект отладки** раскрывающемся списке выберите устройство ARM.  
  
3.  В меню, выберите **Отладка**, **графики**, **Начать диагностику**. (Или нажмите клавиши ALT + F5.)  
  
## <a name="see-also"></a>См. также  
 [Запустите Windows Store apps на удаленном компьютере](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Практическое руководство. Изменение машины воспроизведения диагностики графики](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)



