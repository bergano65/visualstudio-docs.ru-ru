---
title: Создание настраиваемых визуализаторов данных | Документация Майкрософт
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
- vs.debug.visualizer.troubleshoot
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
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a025068d1657d9feb569a77731aa8bab517bae2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568968"
---
# <a name="create-custom-visualizers-of-data"></a>Создание настраиваемых визуализаторов данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [пользовательских создавать визуализаторы данных](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).  
  
Визуализаторы – это компоненты [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] пользовательского интерфейса отладчика. Объект *визуализатор* создает диалоговое окно или другой интерфейс для отображения переменной или объекта способом, подходящим для этого типа данных. Например, HTML-визуализатор интерпретирует строку HTML и отображает результат в том виде, в каком она будет выглядеть в окне браузера; визуализатор точечных рисунков распознает структуру точечного рисунка и отображает его. Некоторые визуализаторы позволяют не только просматривать, но и редактировать данные.  
  
 Отладчик [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] включает шесть стандартных визуализаторов. Это текст, HTML, XML и JSON визуализаторы, которые работают со строковыми объектами; Визуализатор дерева WPF для отображения свойств визуального дерева объекта WPF; и средство визуализации наборов данных, который работает с объектами DataSet, DataView и DataTable. В будущем могут появиться дополнительные визуализаторы, которые будут доступны для загрузки из корпорации Майкрософт, а также сайтов сторонних компаний и сообщества. Кроме того, вы можете создавать собственные визуализаторы и устанавливать их в отладчик [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
> [!NOTE]
>  В **Store** приложений, только стандартные текстовые визуализаторы HTML, XML и JSON поддерживаются. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
 В отладчике для обозначения визуализаторов используется значок лупы. Когда появится значок лупы в **DataTip**, в окне переменных или в **"Быстрая проверка"** диалоговом окне щелкните лупу, чтобы выбрать визуализатор, подходящий для типа данных соответствующего объекта.  
  
 Визуализаторы не поддерживаются в Compact Framework.  
  
> [!NOTE]
>  Визуализаторы отладчика требуют больше прав, чем разрешено приложениям частичного доверия. В результате визуализатор не загрузится, если остановка произошла в коде с частичным доверием. Чтобы отлаживать, используя визуализатор, необходимо запустить код с полным доверием.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Практическое руководство. Написание визуализатора](../debugger/how-to-write-a-visualizer.md)  
  
 [Пошаговое руководство. Написание визуализатора на C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  
  
 [Практическое руководство. Установка визуализатора](../debugger/how-to-install-a-visualizer.md)  
  
 [Практическое руководство. Тестирование и отладка визуализатора](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Справочные сведения о прикладном программном интерфейсе визуализаторов](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Связанные разделы  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)



