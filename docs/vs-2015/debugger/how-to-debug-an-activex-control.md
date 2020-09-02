---
title: Практическое руководство. Отладка элемента управления ActiveX | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704454"
---
# <a name="how-to-debug-an-activex-control"></a>Практическое руководство. отладку элемента управления ActiveX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ПРИМЕЧАНИЕ
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. [в разделе Настройка параметров разработки в Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Чтобы выполнить отладку элемента управления ActiveX, задайте контейнер (исполняемый файл) для элемента управления.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Задание контейнера для сеанса отладки  
  
1. Выберите проект в Обозревателе решений.  
  
2. В меню **Вид** выберите пункт **Страницы свойств**.  
  
3. В диалоговом окне **Страницы свойств проекта** откройте папку **Свойства конфигурации** и выберите категорию **Отладка**.  
  
4. В категории **Отладка** найдите свойство **Команда**.  
  
5. Задайте путь к контейнеру. Например, C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6. Если задать Internet Explorer в качестве контейнера и использовать возможность Active Desktop, введите `/new` в поле **Аргументы команды**.  
  
7. Нажмите кнопку **ОК**.  
  
     Если не задавать контейнер в диалоговом окне **Страницы свойств проекта**, его можно будет задать при запуске отладки. При выборе команды запуска отладки появится диалоговое окно [Исполняемый файл для сеанса отладки](../debugger/executable-for-debugging-session-dialog-box.md). Задайте в диалоговом окне путь к контейнеру.  
  
## <a name="see-also"></a>См. также:  
 [Элементы управления ActiveX](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [Тестирование свойств и событий с помощью тестового контейнера](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)
