---
title: Задача BscMake | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 668d42cdb0bc5cfb8dd344aab51ad0c66a838cd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634517"
---
# <a name="bscmake-task"></a>Задача BscMake

> [!IMPORTANT]
> BscMake больше не используется в интегрированной среде разработки Visual Studio. Начиная с Visual Studio 2008 сведения о просмотре автоматически сохраняются в *SDF*-файле в папке *решения*.

 Заключает в оболочку средство "Программа управления сведениями о просмотре Майкрософт" (*bscmake.exe*).  Средство *bscmake.exe* создает файл сведений о просмотре (*BSC*-файл) из исходных файлов браузера (*SBR*-файлов), созданных во время компиляции. Используйте **обозреватель объектов** для просмотра *BSC*-файла. Дополнительные сведения см. в разделе [Справочник по BSCMAKE](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Параметры

 В следующей таблице описываются параметры задачи **BscMake**. Большинство параметров задач соответствуют параметрам командной строки.

|Параметр|Description|
|---------------|-----------------|
|**AdditionalOptions**|Необязательный параметр **String** .<br /><br /> Список параметров, как указано в командной строке. Например, /\<параметр1> /\<параметр2> /\<параметр#>. Этот параметр используется для указания параметров, не представленных каким-либо другим параметром задачи **BscMake**.<br /><br /> Дополнительные сведения см. в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|
|**OutputFile**|Необязательный параметр **String** .<br /><br /> Задает имя файла, которое переопределяет имя выходного файла по умолчанию.<br /><br /> Дополнительные сведения см. в описании параметра **/o** в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|
|**PreserveSBR**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, выполняется недобавочная сборка. Полная недобавочная сборка происходит независимо от того, существует ли *BSC*-файл, и предотвращает усечение *SBR*-файлов.<br /><br /> Дополнительные сведения см. в описании параметра **/n** в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|
|**Источники**|Необязательный параметр **ITaskItem[]** .<br /><br /> Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.|
|**SuppressStartupBanner**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/NOLOGO** в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|
|**TrackerLogDirectory**|Необязательный параметр **String** .<br /><br /> Задает каталог для журнала отслеживания.|

## <a name="see-also"></a>См. также раздел

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
