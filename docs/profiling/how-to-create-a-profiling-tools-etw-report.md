---
title: Практическое руководство. Создание отчета трассировки событий Windows для средств профилирования | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5fe610ea87c492e0bf562fe00145c3abaf76b8ef
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520631"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Практическое руководство. Создание отчета трассировки событий Windows для средств профилирования
Отчет трассировки событий для Windows информирует о событиях трассировки событий Windows, которые были сохранены в ходе сеанса анализа производительности для средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Данные трассировки событий Windows собираются в двоичном *ETL*-файле. Дополнительные сведения об отчете трассировки событий Windows см. в статье [Отчет трассировки событий Windows](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> Отчеты трассировки событий Windows невозможно отобразить в интерфейсе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Сведения о сборе данных трассировки событий Windows с помощью интерфейса [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] см. в статье [Практическое руководство. Сбор данных трассировки событий Windows](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Сведения о сборе данных трассировки событий Windows из командной строки см. в статьях с описанием [средства VSPerfCmd](../profiling/vsperfcmd.md) и [событий](../profiling/events-vsperfcmd.md).

  Отчет трассировки событий Windows можно создать с помощью команды **VSReport/summary:etw**. *ETL*-файл с данными трассировки событий Windows должен располагаться в том же каталоге, что и файл данных профилирования (*VSP* или *VSPS*). По умолчанию отчет создается как *CSV*-файл с разделителями-запятыми. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>Создание отчета трассировки событий Windows

- В окне **командной строки** введите следующую команду:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |Элемент|Описание|
    |-|-|
    |*ToolsPath*|Путь к программе средств профилирования. Дополнительные сведения см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Файл данных профилирования (*VSP* или *VSPS*). Допускаются полные или частичные пути.|
    |Xml|Создает отчет в формате XML.|
