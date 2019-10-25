---
title: 'Предупреждение: Отладка скриптов отключена | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91875a370f6d072cf2dd69807f516b8f1a808461
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728200"
---
# <a name="warning-script-debugging-disabled"></a>Предупреждение. Отладка скриптов отключена
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

## <a name="see-also"></a>См. также
- [Практическое руководство. Присоединение к скрипту](../debugger/how-to-attach-to-script.md)