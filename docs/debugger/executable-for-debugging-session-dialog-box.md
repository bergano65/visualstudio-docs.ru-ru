---
title: Исполняемый файл для сеанса диалоговое окно отладки | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 915f6f7c9ab13fb7cd832df61638fa0e18e853a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="executable-for-debugging-session-dialog-box"></a>Исполняемый файл для сеанса отладки - диалоговое окно
Это диалоговое окно появляется при попытке выполнить отладку библиотеки DLL, для которой не указан исполняемый файл. Visual Studio не может запустить непосредственно библиотеку DLL. Вместо этого Visual Studio запускает указанный исполняемый файл. Отладку библиотеки DLL можно будет выполнить, когда она будет вызвана исполняемым файлом.  
  
 **Имя исполняемого файла**  
 Введите путь к исполняемому файлу, который вызовет отлаживаемую библиотеку DLL.  
  
 **URL-адрес, где проект может быть доступен (только для сервера ATL)**  
 Если выполняется отладка библиотеки DLL сервера ATL, введите URL-адрес, по которому может быть найден проект.  
  
 После того как эти параметры заданы, они хранятся в страницах свойств проекта, поэтому в последующих сеансах отладки повторно задавать эти параметры не потребуется. Если возникнет необходимость в их изменении, можно открыть окно "Страницы свойств" и задать требуемые значения. Дополнительные сведения о задании исполняемого файла для сеанса отладки см. в разделе [отладка библиотек DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка в Visual Studio](../debugger/index.md)  
 [Обзор функций отладчика](../debugger/debugger-feature-tour.md)