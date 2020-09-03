---
title: Поддержка языковой службы для отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c61f7fa7e698e2c01cadb1dbb36a321c6e656e35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195003"
---
# <a name="language-service-support-for-debugging"></a>Поддержка языковой службы для отладки
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Языковая служба может предоставлять функции, поддерживающие отладчик через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> интерфейс. Эти функции включают проверку точек останова и предоставление списка выражений в окне **видимые** .  
  
 Однако для отладки языка требуется средство оценки выражений. Средство оценки выражений отвечает за вычисление выражений для получения значений во время отладки. Дополнительные сведения о реализации вычислителей выражений CLR см. в следующих статьях:  
  
- [Вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
- [Пример средства оценки управляемого выражения](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Выходные данные компилятора  
 Тип компилятора определяет, что необходимо сделать для реализации отладки для вашего языка. Если компилятор предназначен для операционной системы Windows и записывает PDB-файл, можно выполнять отладку программ с помощью машинного модуля отладки кода, интегрированного в Visual Studio. Если компилятор создает MSIL, можно выполнять отладку программ с помощью модуля отладки управляемого кода, который также интегрирован в Visual Studio. Если компилятор предназначен для собственной операционной системы или другой среды выполнения, необходимо написать собственный модуль отладки.  
  
 Дополнительные сведения о реализации отладки для вашего языка см. в разделе [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) в пакете SDK для отладки Visual Studio.
