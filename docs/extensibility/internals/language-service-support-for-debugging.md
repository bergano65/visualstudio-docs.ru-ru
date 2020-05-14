---
title: Служба языковдля отладки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707436"
---
# <a name="language-service-support-for-debugging"></a>Поддержка языковой службы для отладки
Языковая служба может предоставить функции, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> поддерживающие отладчика через интерфейс. Эти функции включают проверку моментов разрыва и предоставление списка выражений в окно **Autos.**

 Тем не менее, для отладки языка необходимо иметь оценщика выражения. Оценщик выражения отвечает за оценку выражений для создания значений во время отладки. Для получения информации о реализации оценщиков выражений CLR, пожалуйста, см.

- [Оценщики экспрессии CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Образец управляемого оценщика экспрессии](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Выходные данные компилятора
 Тип компилятора определяет, что нужно сделать для реализации отладки для вашего языка. Если компилятор нацелился на операционную систему Windows и записывает файл .pdb, можно отладить программы с помощью отладки кода с помощью движка отладки кода, интегрированного в Visual Studio. Если компилятор производит промежуточный язык Microsoft (MSIL), вы можете отладить программы с управляемым движком отладки кода, который также интегрирован в Visual Studio. Если компилятор нацелен на проприетарную операционную систему или другую среду выполнения, вам необходимо написать свой собственный отладку.

 Для получения дополнительной информации о реализации [Getting Started](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) отладки для вашего языка, см.
