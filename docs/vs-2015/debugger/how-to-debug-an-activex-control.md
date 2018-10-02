---
title: 'Практическое: Debug an ActiveX Control | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc47ba913ba9da1ecfe8e0df34894c31545e1734
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562213"
---
# <a name="how-to-debug-an-activex-control"></a>Практическое руководство. Отладка элемента управления ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: Debug an ActiveX Control](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-an-activex-control).  
  
ПРИМЕЧАНИЕ.]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Чтобы выполнить отладку элемента управления ActiveX, задайте контейнер (исполняемый файл) для элемента управления.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Задание контейнера для сеанса отладки  
  
1.  Выберите проект в Обозревателе решений.  
  
2.  Из **представление** меню, выберите **страницы свойств**.  
  
3.  В **страницы свойств проекта** , открытом окне **свойства конфигурации** и выберите **Отладка**.  
  
4.  В разделе **Отладка** категории, найдите **команда** свойство.  
  
5.  Задайте путь к контейнеру. Например, C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6.  Если указать Internet Explorer в качестве контейнера, и вы используете Active Desktop, введите `/new` в **аргументы команды** поле.  
  
7.  Нажмите кнопку **ОК**.  
  
     Если вы не укажете контейнера в **страницы свойств проекта** диалоговом окне можно указать контейнер при запуске отладки. При выборе команды запуска отладки [исполняемый файл для отладки-диалоговое окно сеанса](../debugger/executable-for-debugging-session-dialog-box.md) отображается. Задайте в диалоговом окне путь к контейнеру.  
  
## <a name="see-also"></a>См. также  
 [Элементы управления ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Тестирование свойств и событий с использованием тестового контейнера](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)



