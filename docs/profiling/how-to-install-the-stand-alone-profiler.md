---
title: Установка автономного профилировщика | Документация Майкрософт
description: Узнайте, как установить автономный профилировщик, который можно использовать, не устанавливая Visual Studio. Есть случаи, когда не следует устанавливать Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c9ff3fccecb785feb222eeadf653d8fd9d8c17df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897696"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Практическое руководство. Установка автономного профилировщика
В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предусмотрен автономный профилировщик для запуска из командной строки, который может выполняться без установки интегрированной среды разработки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Подобная ситуация возникает в том случае, если для установки среды разработки на компьютере нет необходимости или возможности. Например, среду разработки не следует устанавливать на рабочем веб-сервере.

> [!NOTE]
> При использовании автономного профилировщика для сбора данных по производительности веб-сайта ASP.NET программа командной строки [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) предпочтительнее программы [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-install-the-stand-alone-profiler"></a>Установка автономного профилировщика

1. Скачайте [средства оценки производительности для Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Найдите автономный установщик (*vs_standaloneprofiler.exe*) в папке, в которую были скачаны средства оценки производительности, и запустите его.

2. Добавьте путь к файлу *vsinstr.exe* в системный путь.

   > [!NOTE]
   > Сведения о пути к средствам профилирования см. в статье [Указание пути к программам командной строки средств профилирования](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования программ командной строки профилировщика необходимо добавить путь к программам в переменную среды PATH окна командной строки или в саму команду.

3. В командной строке введите **VSInstr**.

   > [!NOTE]
   > Если отображаются сведения об использовании файла vsinstr.exe, установка выполнена правильно. Если выводится сообщение об ошибке, в котором указывается, что файл vsinstr.exe или одна из его зависимостей не найдены, проверьте правильность задания путей, как описано в шаге 2.

4. Настройте сервер символов, присвоив переменной **_NT_SYMBOL_PATH** значение **symsrv\*symsrv.dll\*c:\localcache\*https://msdl.microsoft.com/download/symbols** .

5. После настройки сервера символов с помощью системных переменных среды запустите средства профилирования из нового окна командной строки. Это позволит применить новые переменные среды. В окне командной строки введите следующую команду:

    **start %COMSPEC%**

   > [!NOTE]
   > Подробные инструкции по настройке пакета сервера символов см. в статье [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md).

6. Для сериализации символов в файл данных профилирования (VSP) используется средство [VSPerfReport](../profiling/vsperfreport.md). Следует использовать параметры **VSPerfReport /summary:all /packsymbols**. Если символы в файл данных не вставлены, убедитесь в том, что переменная среды _NT_SYMBOL_PATH задана.

## <a name="see-also"></a>См. также
- [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Пошаговое руководство: Профилирование из командной строки с помощью метода инструментирования](command-line-profiling-of-stand-alone-applications.md)
- [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
