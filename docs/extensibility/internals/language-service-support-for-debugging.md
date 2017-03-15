---
title: "Поддержка службы языка для отладки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладчик, языковая поддержка"
  - "языковые службы, поддержка отладки"
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Поддержка службы языка для отладки
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Служба языка может предоставлять функции, которые поддерживает отладчик через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> интерфейса. Эти возможности включают проверку точки останова и указания списка выражений для **Видимые** окна.  
  
 Тем не менее необходимо иметь вычислитель выражений для отладки вашего языка. Средство оценки выражений отвечает за оценку выражений и получения значений во время отладки. Сведения о реализации вычислители выражений CLR см. в разделе:  
  
-   [Вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Образец вычислитель управляемых выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## Сообщения компилятора  
 Тип компилятор определяет, что необходимо сделать для выполнения отладки для вашего языка. Если компилятор предназначен для операционной системы Windows и записывает в PDB\-файле, можно отлаживать программы с машинным кодом отладки ядра, который интегрирован в Visual Studio. Если компилятор создает промежуточный язык Microsoft \(MSIL\), с помощью управляемого кода, отладка механизм, который интегрирован в Visual Studio также можно отлаживать программы. Если компилятор предназначен для собственных операционной системы или другой среды, необходимо написать собственный ядро отладки.  
  
 Дополнительные сведения о реализации отладки для вашего языка. в разделе [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) в Visual Studio отладка SDK.