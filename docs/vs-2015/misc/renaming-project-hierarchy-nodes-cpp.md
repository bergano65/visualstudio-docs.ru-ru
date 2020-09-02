---
title: Переименование узлов иерархии проектов (C++) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686588"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Переименование узлов иерархии проекта (C++)
Узел иерархии папок проекта можно переименовать с помощью платформы проекта HierUtil7 для неуправляемого C++. Дополнительные сведения см. в разделе [HierUtil7 Sample](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Развертывание узла иерархии  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Развертывание узла иерархии и переименование папки  
  
1. Выберите узел иерархия с помощью следующего метода:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` — это контейнер иерархии, соответствующий папке и `EXPF_SelectItem` из <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> перечисления. `GUID_MacroExplorer`— Это константа GUID, определенная в всшелл. idl, и является примером `rguidPersistenceSlot` в сигнатуре функции `ExtExpand` , определенной в Hu_node. h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Файл Hu_node. h можно найти в папке, \<installation root> \Program филес\всип 8.0 \ EnvSDK\common\hierutil7:  
  
2. Переименуйте папку, отправляя команду rename с помощью команды. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` является <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> указателем: `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` уникальный идентификатор группы команд `cmdidRename` , которой принадлежит команда, определенная в всшлидс. h.  
  
## <a name="see-also"></a>См. также:  
 [Создание типов проектов](../extensibility/internals/creating-project-types.md)   
 [Примеры VSSDK](../misc/vssdk-samples.md)