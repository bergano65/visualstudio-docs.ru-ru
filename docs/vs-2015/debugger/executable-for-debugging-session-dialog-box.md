---
title: Исполняемый файл для сеанса диалоговое окно "Отладка" | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26a7eabe624b75c2b9ded6d14e6bf7c92505ba2d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753625"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Исполняемый файл для сеанса отладки - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это диалоговое окно появляется при попытке выполнить отладку библиотеки DLL, для которой не указан исполняемый файл. Visual Studio не может запустить непосредственно библиотеку DLL. Вместо этого Visual Studio запускает указанный исполняемый файл. Отладку библиотеки DLL можно будет выполнить, когда она будет вызвана исполняемым файлом.  
  
 **Имя исполняемого файла**  
 Введите путь к исполняемому файлу, который вызовет отлаживаемую библиотеку DLL.  
  
 **URL-адрес, где проект может быть доступен (только для сервера ATL)**  
 Если выполняется отладка библиотеки DLL сервера ATL, введите URL-адрес, по которому может быть найден проект.  
  
 После того как эти параметры заданы, они хранятся в страницах свойств проекта, поэтому в последующих сеансах отладки повторно задавать эти параметры не потребуется. Если возникнет необходимость в их изменении, можно открыть окно "Страницы свойств" и задать требуемые значения. Дополнительные сведения о задании исполняемого файла для сеанса отладки, см. в разделе [отладка библиотек DLL](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)



