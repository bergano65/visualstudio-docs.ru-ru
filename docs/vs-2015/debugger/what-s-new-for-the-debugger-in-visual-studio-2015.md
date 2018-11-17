---
title: Новые возможности отладчика в Visual Studio 2015 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 859233c1c79360f28e306dc0fca7df574cb39ccf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774891"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Новые возможности отладчика в Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сведения о всех новых возможностях отладки и диагностики в Visual Studio 2015 с обновлением 1 см. в [заметках о выпуске Visual Studio 2015 с обновлением 1](https://www.visualstudio.com/news/vs2015-update1-vs#debug).  
  
 Сведения о всех новых возможностях отладки и диагностики в Visual Studio 2015 RTM см. в [заметках о выпуске Visual Studio 2015](https://www.visualstudio.com/news/vs2015-vs#debug).  
  
## <a name="visual-studio-2015-update-1-changes"></a>Изменения в Visual Studio 2015 с обновлением 1  
 Компонент C++ "Изменить и продолжить" поддерживает дополнительные функции. Дополнительные сведения см. в разделе [изменить и продолжить (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Для отладки нарушений доступа Visual C++ новое диалоговое окно исключения указывает указатель, который вызвал исключение. Дополнительные сведения см. в разделах [How Can I Debug an Access Violation?](../debugger/how-can-i-debug-an-access-violation-q.md) и [Улучшения отладки нарушения прав доступа C++ в Visual Studio 2015 г. с обновлением 1](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)  
  
## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Изменения пользовательского интерфейса отладчика и сочетаний клавиш в Visual Studio 2015 RTM  
 Пользовательский интерфейс исключений и точек останова значительно изменился.  
  
### <a name="breakpoints"></a>Точки останова  
 В Visual Studio 2015 добавлен новый способ настройки точек останова — окно **Параметры точки останова** .  
  
 Здесь приводится сводка по основным окнам и сочетаниям клавиш для точек останова.  
  
|Возможности|Расположение меню|Сочетание клавиш|  
|-------------|-------------------|------------|  
|Создание точки останова, переключение точки останова|**Отладка / Переключение точки останова**<br /><br /> контекстное меню в редакторе / **Вставить точку останова**<br /><br /> щелкнуть в области левого поля|F9|  
|Новая точка останова в функции|**Отладка / создать точки останова / точка останова в функции**|В Visual Studio 2015 RTM (с без обновления) используйте сочетание клавиш ALT + F9, B<br /><br /> В Visual Studio 2015 с обновлением 1 и более поздних версий нажмите клавиши CTRL + B|  
|Окно**Точки останова** |**Отладка / Windows / точки останова**|CTRL+ALT+B|  
|**Параметры точки останова**, **Условия**|контекстное меню точки останова / **Условия**|ALT+F9, С|  
|**Параметры точки останова**, **Действия**|контекстное меню точки останова / **Действия**|Сочетание клавиш отсутствует|  
  
 Дополнительные сведения см. в следующих статьях:  
  
1.  [Использование точек останова](../debugger/using-breakpoints.md)  
  
2.  [Новые возможности настройки точек останова](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)  
  
3.  [Возможности настройки точек останова](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)  
  
### <a name="exception-settings"></a>Параметры исключений  
 Новое окно **Параметры исключения** позволяет указать тип обработки исключений для одного исключения или разных категорий исключений.  
  
|Функция|Расположение меню|Сочетание клавиш|  
|-------------|-------------------|------------|  
|Окно**Параметры исключения** |**Отладка / Windows / параметры исключений**|CTRL+ALT+E|  
  
 Дополнительные сведения см. в следующих статьях:  
  
1.  [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)  
  
2.  [Новое окно исключений](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)  
  
### <a name="edit-and-continue"></a>Изменить и продолжить  
 В Visual Studio 2015 г. можно задать команду «Изменить и продолжить» на странице **Сервис / Параметры / Отладка / Общие** . В предыдущих версиях эти параметры были вынесены в отдельную категорию параметров.  
  
### <a name="attach-to-process"></a>Присоединение к процессу  
 В Visual Studio 2015 команда «Присоединение к процессу» доступна только из меню «Отладка». В предыдущей версии команда также была доступна в меню «Сервис». Сочетание клавиш CTRL+ALT+P работает во всех версиях.  
  
## <a name="see-also"></a>См. также  
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)



