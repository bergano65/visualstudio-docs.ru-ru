---
title: Представление "Строки" | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 25dbb0beb600f7f043ae006e09ac48b9b64d613b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773985"
---
# <a name="lines-view"></a>Представление строк
Представление "Строки" доступно только для данных профилировщика, собранных с использованием метода выборки. Представление недоступно для данных, собранных с использованием инструментирования.

 Для данных выборочного профиля представление "Строки" определяет оператор в функции, которая непосредственно выполнялась в момент получения выборки. Для данных памяти .NET представление "Строки" определяет операторы, выделяющие память.

 В исходном файле оператор может занимать несколько строк, а одна строка может включать несколько операторов.

 Оператор определяется следующими данными:

- исходным файлом, который содержит оператор функции;

- функцией, содержащей оператор;

- исходной строкой, с которой начинается оператор;

- знаком исходной строки, с которой начинается оператор;

- исходной строкой, которой заканчивается оператор;

- знаком исходной строки, которой заканчивается оператор.

## <a name="see-also"></a>См. также
- [Представление "Строки"](../profiling/lines-view-sampling-data.md)
- [Представление "Строки" — выборка](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Представление "Строки"](../profiling/lines-view-contention-data.md)
