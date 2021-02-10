---
title: Сбор данных счетчиков производительности Windows | Документация Майкрософт
description: Счетчики Windows используются при профилировании инструментирования. В этой статье приводятся сведения о том, как собирать данные счетчиков Windows и ограничивать анализ одним интервалом.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f1e8f38ee9cb63dfe5a79f0b410e957b4cefaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886214"
---
# <a name="how-to-collect-windows-counter-data"></a>Практическое руководство. Сбор данных счетчиков производительности Windows

Счетчики Windows являются счетчиками производительности системы. Сбор данных с них можно выполнять через заданные интервалы во время профилирования. В представлении "Метки" отчета средств профилирования строка имеет метку **AutoMark** для каждого интервала сбора данных. Строка содержит столбцы, которые описывают значения счетчиков производительности в этом интервале. Чтобы ограничить период анализа интервалом между двумя определенными метками, выберите метки, щелкните их правой кнопкой мыши и выберите в контекстном меню команду **Фильтрация по** > **Метки**.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-collect-windows-counter-data"></a>Сбор данных счетчиков производительности Windows

1. В обозревателе производительности щелкните правой кнопкой мыши сеанс, для которого требуется настроить счетчики Windows, и выберите **Свойства**.

2. В окне **Страницы свойств** щелкните страницу **Счетчики Windows**.

3. Установите флажок **Сбор счетчиков Windows**.

4. В текстовом поле **Интервал сбора (мс)** введите интервал времени.

5. Выберите категорию в раскрывающемся списке **Категория счетчика**.

6. Выберите экземпляр в раскрывающемся списке **Экземпляр**.

7. Выберите счетчики, которые будут использоваться при профилировании приложения.

8. Нажмите кнопку **Применить**.

## <a name="see-also"></a>См. также

[Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
[Свойства сеанса анализа производительности](../profiling/performance-session-properties.md)
[Счетчики ЦП и Windows](../profiling/cpu-and-windows-counters.md)
