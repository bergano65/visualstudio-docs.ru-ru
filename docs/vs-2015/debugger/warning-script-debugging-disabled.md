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
ms.openlocfilehash: 36065120dc636f0004f0e00d8b17a0059a680723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161374"
---
# <a name="warning-script-debugging-disabled"></a>Предупреждение: Отладка скриптов отключена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладка скриптов в Internet Explorer в настоящий момент отключена  
  
 Это предупреждение появляется при попытке отладки скрипта при выключенной отладке скриптов в Internet Explorer. По соображениям безопасности отладка скриптов в Internet Explorer отключена по умолчанию.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Включение отладки скриптов в Internet Explorer  
  
1. В меню Internet Explorer **Сервис** выберите **Свойства обозревателя**.  
  
2. В диалоговом окне **Свойства обозревателя** перейдите на вкладку **Дополнительно** .  
  
3. На вкладке **Дополнительно** найдите в поле **Параметры** категорию **Обзор**.  
  
4. Снимите флажок **Отключить отладку скриптов (Internet Explorer)** .  
  
5. Нажмите кнопку **ОК**.  
  
6. Выйдите и повторно запустите Internet Explorer.  
  
     Теперь новые параметры вступят в силу.  
  
## <a name="see-also"></a>См. также:  
 [Практическое руководство. Присоединение к скрипту](../debugger/how-to-attach-to-script.md)
