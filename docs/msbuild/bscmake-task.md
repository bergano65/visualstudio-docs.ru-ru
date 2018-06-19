---
title: Задача BscMake | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
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
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4f10d43fec6ad02cd83debac100add989f65d2df
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31568036"
---
# <a name="bscmake-task"></a>Задача BscMake
> [!IMPORTANT]
>  BSCMAKE больше не используется в интегрированной среде разработки Visual Studio. Начиная с Visual Studio 2008, сведения о просмотре автоматически сохраняются в SDF-файле в папке решения.  
  
 Заключает в оболочку средство «Программа управления сведениями о просмотре Майкрософт» (bscmake.exe).  Средство bscmake.exe создает файл сведений о просмотре (BSC-файл) из исходных файлов браузера (SBR-файлов), созданных во время компиляции. Используйте **обозреватель объектов** для просмотра BSC-файла. Дополнительные сведения см. в разделе [Справочник по BSCMAKE](/cpp/build/reference/bscmake-reference).  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описываются параметры задачи **BscMake**. Большинство параметров задач соответствуют параметрам командной строки.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|**AdditionalOptions**|Необязательный параметр типа **String**.<br /><br /> Список параметров, как указано в командной строке. Например, "/*параметр_1* /*параметр_2* /*параметр_#*". Этот параметр используется для указания параметров, не представленных каким-либо другим параметром задачи **BscMake**.<br /><br /> Дополнительные сведения см. в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**OutputFile**|Необязательный параметр типа **String**.<br /><br /> Задает имя файла, которое переопределяет имя выходного файла по умолчанию.<br /><br /> Дополнительные сведения см. в описании параметра **/o** в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**PreserveSBR**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, выполняется недобавочная сборка. Полная недобавочная сборка происходит независимо от того, существует ли BSC-файл, и предотвращает усечение SBR-файлов.<br /><br /> Дополнительные сведения см. в описании параметра **/n** в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**Sources**|Необязательный параметр **ITaskItem[]**.<br /><br /> Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.|  
|**SuppressStartupBanner**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/NOLOGO** в разделе [Параметры BSCMAKE](/cpp/build/reference/bscmake-options).|  
|**TrackerLogDirectory**|Необязательный параметр типа **String**.<br /><br /> Задает каталог для журнала отслеживания.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)