---
title: Сбор данных трассировки событий Windows | Документация Майкрософт
description: Сведения о том, как использовать трассировку событий для Windows (ETW), чтобы определить, где в приложении возникают проблемы с производительностью. Для просмотра данных используется VSPerfReport.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 77ddd22450786091c5240f26213633a7935c03dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886292"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Практическое руководство. Сбор данных трассировки событий Windows

Трассировка событий Windows (ETW) является эффективным средством трассировки на уровне ядра, которое позволяет профилировщику регистрировать события ядра или приложения. Данные, полученные от поставщика событий, можно просматривать только с помощью параметра /**Summary:ETW** программы командной строки [VSPerfReport](../profiling/vsperfreport.md). Этот отчет можно использовать для определения наличия проблем производительности в приложении.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Включение поставщиков трассировки событий

1. В **обозревателе производительности** щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Свойства**.

2. В окне **Страницы свойств** щелкните свойства **События Windows**.

3. В списке **Выберите поставщик трассировки для сбора данных** выберите поставщики событий для использования при профилировании приложения.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
