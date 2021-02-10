---
title: Отчет операций диска (представление "Потоки") | Документы Майкрософт
description: В отчете операций диска показаны дисковые операции ввода-вывода в каналах диска. Сведения о том, какие сведения регистрируются для каждой операции доступа к диску.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a6b0e15257d67e1d7ff1aaef14c2ebfff3775d6a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923720"
---
# <a name="disk-operations-report-threads-view"></a>Отчет операций диска (представление потоков)
В отчете операций диска показаны дисковые операции ввода-вывода в каналах диска.

 Для каждого типа доступа к диску, выполняемого от имени процесса, профилируемого в текущем периоде, выводятся следующие сведения:

- имя и идентификатор процесса, который обращался к диску;

- идентификатор потока, который обращался к диску;

- имя файла, к которому был получен доступ;

- число операций чтения на файл;

- количество считанных байтов;

- задержка чтения в миллисекундах;

- число операций записи;

- число записанных байтов;

- задержка записи в миллисекундах.

## <a name="see-also"></a>См. также
- [Представление потоков](../profiling/threads-view-parallel-performance.md)