---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-vsct-file
title: "Изменение с помощью изолированной оболочки. Vsct-файле | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3290e33ac473c6914437f8ef036ec8047f46e063
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Изменение с помощью изолированной оболочки. Vsct-файла
Проект пользовательского интерфейса для проекта изолированной оболочки Visual Studio содержит vsct-файл, который позволяет указать, какие группы приложений и отдельных команд доступны в приложении. Ниже приведен фрагмент из неизмененного vsct-файл.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 По умолчанию включены большинство команд и группы команд. Чтобы исключить команды или группы команд, просто снимите комментарии, команды или группы.  
  
 Например, чтобы удалить следующую область и предыдущих панели команд, раскомментируйте `No_PaneNextPaneCommand` и `No_PanePrevPaneCommand` записи:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Более подробные пример этих настроек см. в разделе [Пошаговое руководство: создание базового приложения Isolated Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Файлы, на которые имеются ссылки  
 Vsct-файл по умолчанию для приложения ссылается на следующие файлы. Эти файлы расположены в подкаталоге \VisualStudioIntegration\Common\Inc\ каталога установки Visual Studio SDK.  
  
|Файл|Описание|  
|----------|-----------------|  
|wbids.h|Удостоверения пользовательского интерфейса для Web Обзор пакета.|  
|AppIDCmdUsed.vsct|Таблицы команд для основных элементов пользовательского интерфейса Visual Studio.|  
|EmulatorCmdUsed.vsct|Таблицы команд для Emacs и краткое описание элементов пользовательского интерфейса редактора эмуляции.|  
|Vsdebugguids.h|Определяет идентификаторы GUID команды, страница «Параметры» и другие функции отладчика Visual Studio.|  
|VsDbgCmdUsed.vsct|Таблицы команд для отладчика.|  
  
 Файл AppIDCmdUsed.vsct содержит элементы пользовательского интерфейса Visual Studio, основанные на символы, определенные в vsct-файле приложения.  
  
 Дополнительные сведения см. в разделе [проектирование таблицы команд XML (. Файлы Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) и [Справочник по схеме VSCT XML](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>См. также  
 [Изолированная оболочка Visual Studio](../extensibility/visual-studio-isolated-shell.md)