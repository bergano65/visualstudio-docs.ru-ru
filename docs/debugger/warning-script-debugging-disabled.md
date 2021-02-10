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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 052445b1dbb69c433220caf5764413e04f0909fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884004"
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