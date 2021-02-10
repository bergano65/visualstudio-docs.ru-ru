---
title: Использование средств профилирования из командной строки | Документы Майкрософт
description: Используйте средства профилирования Visual Studio из командной строки для профилирования приложений в командной строке и автоматизации этого процесса с помощью пакетных файлов и скриптов.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6cfb8f26486c731d3900522d72ac62ff6997005e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885954"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Использование Средств профилирования из командной строки
С помощью программ командной строки средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно выполнять профилирование приложений в командной строке и автоматизировать этот процесс с помощью пакетных файлов и скриптов. Кроме того, с помощью командной строки можно создавать файлы отчетов. Для сбора данных на компьютерах без установленной системы [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно использовать упрощенный автономный профилировщик.

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. статью [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Стандартные задачи

| Задача | См. также |
| - | - |
| **Назначение расположения символов**. Для отображения имен функций и параметров у профилировщика должен быть доступ к профилируемым двоичным файлам символов (*PDB*). К числу этих файлов должны относиться файлы символов операционной системы Майкрософт и приложений, данные для которых должны отображаться в результатах анализа. Чтобы убедиться в наличии правильных двоичных *PDB*-файлов, можно воспользоваться общедоступным сервером символов Майкрософт. | -   [Практическое руководство. Определение расположения файлов символов с помощью командной строки](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **Профилирование приложения**. Программы командной строки и параметры, используемые для профилирования целевого приложения, зависят от типа приложения, метода профилирования и типа приложения (управляемый или машинный код). | -   [Использование методов профилирования из командной строки](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Профилирование служб](../profiling/command-line-profiling-of-services.md) |
| **Создание отчетов в формате XML и CSV**. При профилировании в командной строке создаются файлы данных, которые можно просматривать в интерфейсе [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Кроме того, файлы данных в формате *XML* и файлы данных с разделителями-запятыми (*CSV*) можно создавать с помощью программы командной строки VSPerfReport. | -   [Создание отчетов профилировщика из командной строки](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Профилирование кода на компьютерах без Visual Studio**. С помощью автономного профилировщика средств профилирования можно собирать данные для приложений на компьютерах без установленной системы [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. | -   [Практическое руководство. Установка автономного профилировщика](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>Справочник
- [Справочник по Средствам профилирования из командной строки](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>См. также
- [Обозреватель производительности](../profiling/performance-explorer.md)
