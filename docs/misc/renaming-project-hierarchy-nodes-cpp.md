---
title: "Переименование узлов иерархии проекта (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "образец HierUtil7 [пакет SDK для Visual Studio], переименование узлов проекта"
  - "узлы проекта, переименование в образце HierUtil7"
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Переименование узлов иерархии проекта (C++)
Можно переименовать узел иерархии папок проекта с помощью платформы проекта для автономного HierUtil7 C\+\+.  Дополнительные сведения см. в разделе [HierUtil7 Sample](http://msdn.microsoft.com/ru-ru/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## Развернуть узел иерархии  
  
#### Развернуть узел иерархии и переименование папки  
  
1.  Выберите узел иерархии с помощью следующего приема:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` контейнер иерархии, соответствующая папке и  `EXPF_SelectItem` от  <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> перечисление.  `GUID_MacroExplorer` константа, определенная в Vsshell.idl GUID и пример  `rguidPersistenceSlot` в сигнатуре функции  `ExtExpand`определяется в Hu\_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Файл можно найти в папке, Hu\_node.h \<корневой каталог установки\>\\ Program files \\ 8,0 \\ EnvSDK VSIP \\ общее \\ hierutil7:  
  
2.  Переименуйте папку, создать команду переименовать с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` a  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> указатель.  `<IVsUIShell>``srpVsUIShell`.  `guiVSStd97` уникальный идентификатор группы команд, к которой команда  `cmdidRename` принадлежит определяется в Vsshlids.h.  
  
## См. также  
 [Создание типов проектов](../extensibility/internals/creating-project-types.md)   
 [Примеры VSSDK](../misc/vssdk-samples.md)