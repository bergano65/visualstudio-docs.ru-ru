---
title: 'Предупреждение: Отладка скриптов отключена | Документация Майкрософт'
description: Предупреждение "Отладка скриптов отключена" появляется при попытке отладки скрипта при выключенной отладке скриптов в Internet Explorer. В этом разделе приводятся инструкции по включению этой функции.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7cc2e03a4efcf9a88675fd3c80f374ff78ba35bb
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149564"
---
# <a name="warning-script-debugging-disabled"></a>Предупреждение: Отладка скриптов отключена
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
- [Практическое руководство. Присоединение к скрипту](attach-to-running-processes-with-the-visual-studio-debugger.md)