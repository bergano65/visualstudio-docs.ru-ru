---
title: Как использовать визуализатор | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778375"
---
# <a name="how-to-use-a-visualizer"></a>Практическое руководство. Использование визуализатора
С помощью визуализатора можно отобразить содержимое переменной или объекта способом, отвечающим типу данных. Вы можете использовать визуализаторы из **подсказок**, окна " **Контрольные значения** ", окна " **видимые** " или " **локальные** ".  
  
 Визуализаторы не поддерживаются в Compact Framework.  
  
> [!NOTE]
> В приложениях **магазина** поддерживаются только стандартные визуализаторы Text, HTML, XML и JSON. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
### <a name="to-open-a-visualizer"></a>Чтобы открыть визуализатор  
  
1. Щелкните значок лупы рядом с именем переменной в **подсказке**, окне **контрольных значений** или в окне " **видимые**", " **локальные**" или " **Быстрый контроль** ".  
  
     Откроется список визуализаторов.  
  
2. Щелкните визуализатор, который необходимо использовать.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Использование визуализатора для управляемого кода при удаленной отладке  
  
- Скопируйте библиотеку DLL визуализатора на удаленный компьютер, прежде чем начать сеанс отладки.  
  
     Путь к библиотеке DLL на удаленном и локальном компьютерах должен быть одинаковым. Этот путь может быть одним из следующих:  
  
     *Путь установки Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     -или-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Версия Visual Studio*`\Visualizers`  
  
## <a name="see-also"></a>См. также:  
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)   
 [Руководство. Написание визуализатора](../debugger/how-to-write-a-visualizer.md)   
 [Просмотр значений данных в подсказках по данным](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)