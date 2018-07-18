---
title: Поддержка службы языка для отладки | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 59c044f6ffc3f2cdf0749f0192f4b8fa458b00cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128663"
---
# <a name="language-service-support-for-debugging"></a>Поддержка службы языка для отладки
Языковая служба может предоставлять функции, поддерживающие отладчика через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> интерфейса. Их число входят проверка точек останова и указания списка выражений для **видимые** окна.  
  
 Тем не менее необходимо иметь вычислитель выражений для отладки вашего языка. Средство оценки выражений отвечает за вычисление выражений для получения значений во время отладки. Сведения о реализации вычислители выражений CLR см. в разделе:  
  
-   [Вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Образец вычислитель выражений управляемого](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Сообщения компилятора  
 Тип компилятор определяет, что необходимо сделать для выполнения отладки для выбранного языка. Если компилятор предназначен для операционной системы Windows и записывает в PDB-файле, можно отлаживать программы с машинным кодом, отладка ядра, который интегрирован в Visual Studio. Если компилятор создает промежуточный язык Майкрософт (MSIL), можно отлаживать программы с использованием управляемого кода, отладка механизм, который также интегрируется в Visual Studio. Если компилятор предназначен для собственных операционной системы или другой среды, необходимо написать собственный ядро отладки.  
  
 Дополнительные сведения о реализации отладки для конкретного языка см. в разделе [Приступая к работе](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) в Visual Studio пакет SDK для отладки.