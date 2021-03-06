---
title: Сбор данных взаимодействия уровней | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e01259fdd23e60a1408addc10a6af3a12479c9f2
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772822"
---
# <a name="collect-tier-interaction-data"></a>Сбор данных о взаимодействии уровней

Профилирование уровневого взаимодействия позволяет получить дополнительные сведения о времени выполнения функций многоуровневых приложений, взаимодействующих с базой данных посредством служб ADO.NET. Данные собираются только для синхронных вызовов функций.

**Выпуски Visual Studio**

Сведения о профилировании уровневого взаимодействия можно собирать с помощью любого выпуска Visual Studio. Но данные профилирования уровневого взаимодействия можно просматривать только в Visual Studio Enterprise.

**Windows 8 или Windows Server 2012**

Чтобы собрать данные об уровневом взаимодействии на классических приложениях Windows 8 и приложениях Windows Server 2012, необходимо использовать метод инструментирования. Вы не можете собрать данные о взаимодействии уровней для приложений универсальной платформы Windows. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Данные об уровневом взаимодействии можно включить во все методы профилирования на других поддерживаемых версиях Windows.

**Мастер производительности**

Из-за ошибки в мастере производительности, необходимо добавить параметр коллекции данных об уровневом взаимодействии в сеанс профилирования из Обозревателя производительности. Необходимо также добавить проект, исполняемый файл или веб-сайт к узлу целевого объекта в "Обозревателе производительности".

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Добавление данных взаимодействия уровней в сеанс профилирования с помощью страниц свойств сеанса анализа производительности

1. В обозревателе производительности в контекстном меню выберите пункт **Свойства**.

2. Выберите страницу **Взаимодействия уровня** и установите флажок **Включить профилирование взаимодействия уровней**.

3. В обозревателе производительности выделите узел **Целевые объекты**, а затем укажите проект, исполняемый файл или веб-сайт, который необходимо профилировать.

## <a name="see-also"></a>См. также

[Представление "Взаимодействие между уровнями"](../profiling/tier-interactions-view.md)
