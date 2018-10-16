---
title: Создание пользовательских представлений данных в отладчике | Документация Майкрософт
ms.custom: ''
ms.date: 06/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bb65aa2b0601315a3f5dec2cc9459af210db3e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177676"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Создание пользовательских представлений данных в отладчике Visual Studio
В отладчике [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предусмотрены разнообразные средства для проверки и изменения состояния программы. Большинство этих средств функционируют только в режиме приостановки.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Создание пользовательских представлений данных в окнах переменных и подсказки по данным
 Многие из [окна отладчика](../debugger/debugger-windows.md), такие как **"Видимые"** и **Watch** windows, позволяют проверять значения переменных при отладке. Можно настроить отображение собственных типов и управляемых объектов в окнах переменных отладчика и в [подсказок по данным](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Это может быть полезно для отображения типов, которые можно создать в собственных приложениях. Дополнительные сведения см. в разделе [Создание настраиваемых представлений собственных объектов](../debugger/create-custom-views-of-native-objects.md) и [Создание настраиваемых представлений управляемых объектов](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Создание настраиваемых визуализаторов  
 Визуализаторы позволяют просмотреть содержимое объекта или переменной более удобным образом. В отладчике Visual Studio визуализатор ссылается на разных окнах, которые можно открыть с помощью значка лупы ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор"). Например, можно использовать HTML-визуализатор для просмотра HTML-строки в том виде, в каком она была бы показана в браузере. Можно получить доступ к визуализаторам из подсказок, окна **Контрольное значение** , окна **Видимые** , окна **Локальные** или диалогового окна **Быстрая проверка** . Дополнительные сведения см. в разделе [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>См. также  
 [Основы отладки](../debugger/getting-started-with-the-debugger.md)   
 [Командное окно](../ide/reference/command-window.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)