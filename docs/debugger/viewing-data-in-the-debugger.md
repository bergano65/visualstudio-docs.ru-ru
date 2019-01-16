---
title: Создание пользовательских представлений данных в отладчике | Документация Майкрософт
ms.date: 01/09/2019
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
ms.openlocfilehash: e5c5466515e0e58fd94d7a949b04d060a90925d1
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227230"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Создание пользовательских представлений данных в отладчике Visual Studio (C#, Visual Basic, C++)

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Отладчик предоставляет множество средств для проверки и изменения состояния программы. Большинство этих средств функционируют только в режиме приостановки.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Создание пользовательских представлений данных в окнах переменных и подсказки по данным

 Многие из [окна отладчика](../debugger/debugger-windows.md), такие как **"Видимые"** и **Watch** windows, позволяют проверять значения переменных. Вы можете настроить как собственные типы управляемых объектов и собственных типов отображаются в окнах переменных отладчика, а также в [подсказок по данным](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Дополнительные сведения см. в разделе [Создание настраиваемых представлений собственных объектов](../debugger/create-custom-views-of-native-objects.md) и [Создание настраиваемых представлений объектов](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Создание настраиваемых визуализаторов

 Визуализаторы позволяют просмотреть содержимое объекта или переменной более удобным образом. В отладчике Visual Studio визуализатор ссылается на разных окнах, которые можно открыть с помощью увеличительное стекло ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор") значок. Например HTML-визуализатор показывает, как строка HTML будет интерпретируются и отображаются в браузере. Можно получить доступ к визуализаторам из подсказок, **Watch** окне **"Видимые"** окно и **"Локальные"** окна. **"Быстрая проверка"** диалоговое окно также предоставляет визуализатора. Дополнительные сведения см. в статье [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>См. также

 [Сначала посмотрим, отладчик](../debugger/debugger-feature-tour.md) [окно командной строки](../ide/reference/command-window.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)