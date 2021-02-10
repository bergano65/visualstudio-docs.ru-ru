---
title: Пошаговое выполнение служб WCF | Документация Майкрософт
description: Пошаговое выполнение служб Windows Communication Foundation (WCF). Если служба WCF находится в том же решении Visual Studio, что и клиент, можно задавать точки останова внутри нее.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5f3a884698586cdd9a89ff62a090f02af3953a91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896642"
---
# <a name="how-to-step-into-wcf-services"></a>Практическое руководство. пошаговую отладку служб WCF
В [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] можно выполнить пошаговую отладку службы WFC. Если служба WFC находится в том же решении [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], что и клиент, можно задавать точки останова внутри службы WCF.

 Для начала работы необходимо включить отладку в файле app.config или Web.config. Сведения о включении отладки и ограничениях на пошаговое выполнение в службах WCF см. в разделе [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Выполнение пошаговой отладки служб WFC

1. Создайте решение [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], которое содержит проекты клиента WFC и службы WFC.

2. В обозревателе решений щелкните правой кнопкой мыши проект клиента WFC и выберите **Назначить запускаемым проектом**.

3. Включите отладку в файле app.config или web.config. Дополнительные сведения см. в разделе [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md).

4. Установите точку останова в то место в проекте клиента, в котором необходимо начать пошаговую отладку. Как правило, точка останова задается непосредственно перед вызовом службы WCF.

5. Проведите выполнение до точки останова, затем начните пошаговую отладку. Отладчик выполнит пошаговую отладку службы автоматически.

## <a name="see-also"></a>См. также
- [Отладка служб WCF](../debugger/debugging-wcf-services.md)
- [Ограничения на отладку WCF](../debugger/limitations-on-wcf-debugging.md)
- [Практическое руководство. Отладка резидентной службы WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)