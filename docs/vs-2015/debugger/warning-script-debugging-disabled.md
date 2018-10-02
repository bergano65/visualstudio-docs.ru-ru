---
title: 'Предупреждение: Отладка скриптов отключена | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91b54b3e9a70284dc1efb03be7adfaa5d1421920
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560214"
---
# <a name="warning-script-debugging-disabled"></a>Предупреждение. Отладка скриптов отключена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [предупреждение: отладка скриптов отключена](https://docs.microsoft.com/visualstudio/debugger/warning-script-debugging-disabled).  
  
Отладка скриптов в Internet Explorer в настоящий момент отключена  
  
 Это предупреждение появляется при попытке отладки скрипта при выключенной отладке скриптов в Internet Explorer. По соображениям безопасности отладка скриптов в Internet Explorer отключена по умолчанию.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Включение отладки скриптов в Internet Explorer  
  
1.  В Internet Explorer **средства** меню, выберите **обозревателя**.  
  
2.  В диалоговом окне **Свойства обозревателя** перейдите на вкладку **Дополнительно** .  
  
3.  На **Дополнительно** найдите **параметры** », вкладка « **Обзор** категории.  
  
4.  Очистить **отключить отладку сценариев (Internet Explorer)**.  
  
5.  Нажмите кнопку **ОК**.  
  
6.  Выйдите и повторно запустите Internet Explorer.  
  
     Теперь новые параметры вступят в силу.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Присоединение к скрипту](../debugger/how-to-attach-to-script.md)



