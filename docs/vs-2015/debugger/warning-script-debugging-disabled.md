---
title: 'Предупреждение: Отладка скриптов отключена | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b44c260e00ae5ef8b0d23e7aede139563ff22d98
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991210"
---
# <a name="warning-script-debugging-disabled"></a>Предупреждение: Отладка скриптов отключена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладка скриптов в Internet Explorer в настоящий момент отключена  
  
 Это предупреждение появляется при попытке отладки скрипта при выключенной отладке скриптов в Internet Explorer. По соображениям безопасности отладка скриптов в Internet Explorer отключена по умолчанию.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Включение отладки скриптов в Internet Explorer  
  
1.  В меню Internet Explorer **Сервис** выберите **Свойства обозревателя**.  
  
2.  В диалоговом окне **Свойства обозревателя** перейдите на вкладку **Дополнительно** .  
  
3.  На вкладке **Дополнительно** найдите в поле **Параметры** категорию **Обзор**.  
  
4.  Снимите флажок **Отключить отладку скриптов (Internet Explorer)**.  
  
5.  Нажмите кнопку **ОК**.  
  
6.  Выйдите и повторно запустите Internet Explorer.  
  
     Теперь новые параметры вступят в силу.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Присоединение к скрипту](../debugger/how-to-attach-to-script.md)
