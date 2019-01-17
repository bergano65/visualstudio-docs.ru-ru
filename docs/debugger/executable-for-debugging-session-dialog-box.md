---
title: Исполняемый файл для сеанса диалоговое окно "Отладка" | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 90278476b2530e80c33440ca6e2dc299be5e9be5
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269791"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Исполняемый файл для сеанса отладки - диалоговое окно

Это диалоговое окно появляется при попытке выполнить отладку библиотеки DLL, для которой не указан исполняемый файл. Visual Studio не может запустить непосредственно библиотеку DLL. Вместо этого Visual Studio запускает указанный исполняемый файл. Можно выполнять отладку библиотеки DLL, при вызове исполняемого объекта.  
  
 **Имя исполняемого файла**  
 Введите путь к исполняемому файлу, который вызовет отлаживаемую библиотеку DLL.  
  
 **URL-адрес, по которому можно получить доступ к проекту (только для ATL-сервера)**  
 Если выполняется отладка библиотеки DLL сервера ATL, введите URL-адрес, по которому может быть найден проект.  
  
 После ввода, эти параметры хранятся в страницах свойств проекта, поэтому не нужно будет вводить их повторно для последующих сеансов отладки. Если возникнет необходимость в их изменении, можно открыть окно "Страницы свойств" и задать требуемые значения. Дополнительные сведения об указании исполняемого файла для сеанса отладки см. в разделе [Отладка библиотек DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>См. также раздел

 [Отладка в Visual Studio](../debugger/index.md)  
 [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)