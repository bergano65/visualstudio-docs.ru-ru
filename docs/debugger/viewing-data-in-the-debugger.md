---
title: Создание пользовательских представлений данных в отладчике | Документация Майкрософт
ms.custom: ''
ms.date: 11/20/2018
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
ms.openlocfilehash: 59e6c1879d5463682ee41d60e3928fce85c74a8d
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305147"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Создание пользовательских представлений данных в отладчике Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Отладчик предоставляет множество средств для проверки и изменения состояния программы. Большинство этих средств функционируют только в режиме приостановки.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Создание пользовательских представлений данных в окнах переменных и подсказки по данным
 Многие из [окна отладчика](../debugger/debugger-windows.md), такие как **"Видимые"** и **Watch** windows, позволяют проверять значения переменных. Вы можете настроить как собственные типы управляемых объектов и собственных типов отображаются в окнах переменных отладчика, а также в [подсказок по данным](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Дополнительные сведения см. в разделе [Создание настраиваемых представлений собственных объектов](../debugger/create-custom-views-of-native-objects.md) и [Создание настраиваемых представлений управляемых объектов](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Создание настраиваемых визуализаторов  
 Визуализаторы позволяют просмотреть содержимое объекта или переменной более удобным образом. В отладчике Visual Studio визуализатор ссылается на разных окнах, которые можно открыть с помощью увеличительное стекло ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "значок визуализатор") значок. Например HTML-визуализатор показывает, как строка HTML будет интерпретируются и отображаются в браузере. Можно получить доступ к визуализаторам из подсказок, **Watch** окне **"Видимые"** окно и **"Локальные"** окна. **"Быстрая проверка"** диалоговое окно также предоставляет визуализатора. Дополнительные сведения см. в статье [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>См. также  
 [Основы отладки](../debugger/getting-started-with-the-debugger.md)   
 [Командное окно](../ide/reference/command-window.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)