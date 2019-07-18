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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41b93ae19afd54b6e22458d1ba12029d5bb93cf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849964"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Исполняемый файл для сеанса отладки - диалоговое окно

Это диалоговое окно появляется при попытке выполнить отладку библиотеки DLL, для которой не указан исполняемый файл. Visual Studio не может запустить непосредственно библиотеку DLL. Вместо этого Visual Studio запускает указанный исполняемый файл. Можно выполнять отладку библиотеки DLL, при вызове исполняемого объекта.

 **Имя исполняемого файла** введите путь к исполняемому файлу, который вызывает библиотеку DLL, при отладке.

 **URL-адрес, где проект может быть доступен (только для сервера ATL)** при отладке DLL сервера ATL, введите URL-адрес где проект может быть найден.

 После ввода, эти параметры хранятся в страницах свойств проекта, поэтому не нужно будет вводить их повторно для последующих сеансов отладки. Если возникнет необходимость в их изменении, можно открыть окно "Страницы свойств" и задать требуемые значения. Дополнительные сведения об указании исполняемого файла для сеанса отладки см. в разделе [Отладка библиотек DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>См. также

- [Отладка в Visual Studio](../debugger/index.md)
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)