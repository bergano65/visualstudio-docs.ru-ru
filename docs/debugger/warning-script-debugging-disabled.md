---
title: "Предупреждение. Отладка скриптов отключена | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Предупреждение. Отладка скриптов отключена
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Отладка скриптов в Internet Explorer в настоящий момент отключена  
  
 Это предупреждение появляется при попытке отладки скрипта при выключенной отладке скриптов в Internet Explorer.  По соображениям безопасности отладка скриптов в Internet Explorer отключена по умолчанию.  
  
### Включение отладки скриптов в Internet Explorer  
  
1.  В меню Internet Explorer **Сервис** выберите **Свойства обозревателя**.  
  
2.  В диалоговом окне **Свойства обозревателя** перейдите на вкладку **Дополнительно**.  
  
3.  На вкладке **Дополнительно** найдите в поле **Параметры** категорию **Обзор**.  
  
4.  Снимите флажок **Отключить отладку скриптов \(Internet Explorer\)**.  
  
5.  Нажмите кнопку **ОК**.  
  
6.  Выйдите и повторно запустите Internet Explorer.  
  
     Теперь новые параметры вступят в силу.  
  
## См. также  
 [Практическое руководство. Присоединение к скрипту](../debugger/how-to-attach-to-script.md)