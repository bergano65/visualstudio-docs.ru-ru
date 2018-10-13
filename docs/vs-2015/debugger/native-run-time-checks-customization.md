---
title: Настройка проверок собственного выполнения | Документация Майкрософт
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
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 906aca3071c9abc6bd06ac1f0dc4d75bd1920a61
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300889"
---
# <a name="native-run-time-checks-customization"></a>Настройка проверок во время выполнения машинного кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При выполнении компиляции с **/RTC** (проверки времени выполнения) или использовать `runtime_checks` директивы pragma библиотеки времени выполнения C предоставляет проверки времени выполнения в машинном коде. В некоторых случаях необходимо настроить проверки времени выполнения:  
  
-   для направления сообщений о проверке, осуществляемой во время выполнения, в файл или в другое место назначения, отличающиеся от используемого по умолчанию;  
  
-   чтобы определить место назначения для сообщения о проверке, осуществляемой во время выполнения отладчиком стороннего поставщика;  
  
-   для представления сообщений о проверке во время выполнения из программы, скомпилированной с рабочей версией библиотеки времени выполнения языка C. Для представления сообщения об ошибке во время выполнения окончательные версии библиотеки не используют `_CrtDbgReportW`. Вместо этого они отображают **Assert** диалоговое окно для каждой ошибки времени выполнения.  
  
 Для настройки процесса проверки ошибок во время выполнения можно:  
  
-   написать функцию, сообщающую об ошибке времени выполнения. Дополнительные сведения см. в разделе [как: написать функцию отчетов во время выполнения ошибки](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
-   настроить место назначения для сообщения об ошибке;  
  
-   запросить сведения об ошибках проверок времени выполнения;  
  
## <a name="customize-the-error-message-destination"></a>Настройка места назначения для сообщения об ошибке  
 Если для уведомления об ошибках используется функция `_CrtDbgReportW`, то для определения места назначения сообщений об этих ошибках можно использовать `_CrtSetReportMode`.  
  
 Когда применяется пользовательская функция, сообщающая об ошибках, для связывания ошибки и типа сообщения следует использовать функцию `_RTC_SetErrorType`.  
  
## <a name="query-for-information-about-run-time-checks"></a>Запрос сведений о проверках времени выполнения  
 `_RTC_NumErrors` возвращает количество типов ошибок, обнаруженных в процессе проверки во время выполнения. Для получения краткого описания каждой ошибки можно использовать цикл от 0 до возвращенного `_RTC_NumErrors` значения, передавая номер итерации на каждом шаге в функцию `_RTC_GetErrDesc`. Дополнительные сведения см. в разделе [_RTC_NumErrors](http://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) и [_RTC_GetErrDesc](http://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>См. также  
 [Практическое: проверок во время выполнения машинного кода](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](http://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)





