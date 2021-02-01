---
title: 'Командная строка профилирования: создание переносимых файлов данных'
description: Чтобы упростить общий доступ к данным профилирования, используйте программу командной строки VSPerfReport в целях внедрения символов для сеанса профилирования в VSP-файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5df9f14fecce23eb72d08dcba87dee360269e078
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718971"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Создание переносимых файлов данных профилирования в командной строке
Чтобы упростить общий доступ к данным профилирования, вы можете использовать программу командной строки [VSPerfReport](../profiling/vsperfreport.md) в целях внедрения символов для сеанса профилирования в *VSP*-файл.

 Вы также можете создать файл предварительно проанализированных данных профилирования (*VSPS*), который меньше по размеру и быстрее загружается в интегрированной среде разработки.

> [!NOTE]
> Убедитесь, что файлы символов (*PDB*) доступны для **VSPerfReport**. Дополнительные сведения см. в разделе [Практическое руководство. Определение расположения файлов символов с помощью командной строки](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Дополнительные сведения о пути к **VSReport** см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Данные профилирования в *VSPS*-файле невозможно отфильтровать.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Внедрение символов для сеанса профилирования в файл данных профилирования (*VSP*)

- В окне командной строки введите следующую команду:

   \<Path><strong>VSPerfReport \<</strong>VSP-файл> **/PackSymbols**

   По умолчанию *VSPS*-файл имеет базовое имя *VSP*-файла. Вы можете указать альтернативное имя с помощью параметра **Вывод**.

### <a name="to-create-a-summary-profiling-data-file"></a>Создание сводного файла данных профилирования

- В окне командной строки введите следующую команду:

   \<Path><strong>VSPerfReport \<</strong>VSP-файл> **/SummaryFile** [ **/Output:** \<File Name>]

   По умолчанию *VSPS*-файл имеет базовое имя *VSP*-файла. Вы можете указать альтернативное имя с помощью параметра **Вывод**.
