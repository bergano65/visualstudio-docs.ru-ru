---
title: "Решение (. Файл SLN) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d9b2d052f86cf76dcd9e2f97f2ee03eaf07dcf5b
ms.lasthandoff: 02/22/2017

---
# <a name="solution-sln-file"></a>Решение (. Файл SLN)
Это решение представляет собой структуру для организации проектов в Visual Studio. Решения хранит сведения о состоянии для проектов в (текстовый, общие) с расширением SLN и SUO (решение двоичных, пользовательские параметры)-файлы. Дополнительные сведения о SUO-файлы в разделе [пользовательских параметров решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Если в результате ссылаться в SLN-файл загружается VSPackage, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>для чтения в файле с расширением SLN.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>  
  
 SLN-файл содержит текстовой информации, в среде используется для поиска и загрузки параметры имя значение для материализованных данных и пакеты VSPackage, оно ссылается на проект. При открытии решения среды циклически `preSolution`, `Project`, и `postSolution` информацию в файле SLN-файл для загрузки решения, проекты в решении, а все сохраненные данные присоединен в решение.  
  
 Файл каждый проект содержит дополнительные сведения, чтение средой для заполнения иерархии с элементами этого проекта. Сохранение данных иерархии контролируются проекта; данные не хранятся обычно в файле с расширением SLN несмотря на то, что намеренно может записывать информацию проекта в SLN-файл, если вы решите сделать это. Дополнительные сведения, относящиеся к сохраняемости см. в разделе [долговременного хранения проекта](../../extensibility/internals/project-persistence.md) и [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Содержимое файла решения  
 SLN-файл состоит из нескольких разделов, как показано в следующем коде.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Загружено решение, среда выполняет следующую последовательность задач.  
  
1.  Среда считывает общий раздел SLN-файл и обрабатывает все разделы, помеченные `preSolution`. В этом случае является одним из таких операторов:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Когда считывает среды `GlobalSection('name')` тега, он сопоставляет имя VSPackage, используя реестр. Имя ключа должен существовать в разделе реестра [HKLM\\<Application id="" registry=""></Application>\>\SolutionPersistence\AggregateGUIDs]. Значение по умолчанию ключей — идентификатор GUID пакета (REG_SZ) VSPackage, который написал записи.  
  
2.  Среде загрузки VSPackage, вызовы `QueryInterface` в VSPackage для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>интерфейс и вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>метод с данными в разделе, данные можно хранить VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Среде этот процесс повторяется для каждого `preSolution` раздел.  
  
3.  Среды итерацию блоки сохранения проекта. В этом случае существует один проект.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Данная инструкция содержит уникальный идентификатор GUID проекта и GUID типа проекта. Эта информация используется средой для поиска файла проекта или файлы, принадлежащие к решению и VSPackage, необходимые для каждого проекта. Идентификатор GUID, переданный в проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>для загрузки определенного VSPackage, связанные с проектом, затем проект загружен в VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> В этом случае VSPackage, который загружается для данного проекта является Visual Basic.  
  
     Каждый проект может сохранить проект уникальный идентификатор экземпляра, чтобы он был доступен при необходимости, другие проекты в решении. В идеале Если в системе управления версиями решения и проекты, путь к проекту следует относительно пути к решению. При загрузке решения файлы проекта не может быть на компьютере пользователя. Когда файл проекта, хранящиеся на сервере по отношению к файлу решения, сравнительно просто файл проекта, чтобы найти и скопировать на компьютер пользователя. Затем копирует и загружает все файлы, необходимые для проекта.  
  
4.  На основании информации, содержащейся в разделе проект SLN-файл, среде загружает каждый файл проекта. Сам проект отвечает за заполнение иерархии проекта и загрузки все вложенные проекты.  
  
5.  После обработки всех разделов SLN-файл, решение отображается в обозревателе решений и готов для изменения пользователем.  
  
 Если не удается загрузить, любой VSPackage, реализующий проекта в решении <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>вызывается метод, и каждый проект в решении является возможность игнорировать изменения он может во время загрузки.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> При возникновении ошибки синтаксического анализа столько информации сохраняется с файлами решения и среде отображает диалоговое окно предупреждение о повреждении решения.  
  
 При сохранении или закрытии решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>метод вызывается и передается в иерархию, чтобы увидеть, были ли внесены изменения в решение, необходимо указать в файле с расширением SLN.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Значение null, передаваемые в `QuerySaveSolutionProps` в <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, указывает, что сведения о сохраняются для решения.</xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> Если значение не равно null, сохраненной информации — для определенного проекта, определяется указатель <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
 Если имеется информация для сохранения, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>интерфейс вызывается с указателем на <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>метод.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>Средой для получения пары «имя значение» из затем вызывается метод `IPropertyBag` интерфейса и записывать данные в файл с расширением SLN.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>  
  
 `SaveSolutionProps`и `WriteSolutionProps` объекты называются рекурсивно средой для получения сведений, которые будут сохраняться с `IPropertyBag` интерфейс, пока все изменения были введены в SLN-файл. Таким образом можно гарантировать, что данные будут сохранены с решения и доступен следующий раз при открытии решения.  
  
 Для просмотра, если у него есть все, чтобы сохранить файл с расширением SLN перечисляется каждый загрузки VSPackage. Это только во время загрузки, которые запрашиваются разделов реестра. Среды знает о загруженных пакетов, поскольку они находятся в памяти во время сохранения решения.  
  
 Только SLN-файл содержит записи в `preSolution` и `postSolution` разделы. Существует не подобных разделов в файле SUO так, как оно должно правильно загрузить эти данные. SUO-файл содержит параметры, относящиеся к пользователю, например частных заметок, которые не предназначены для общих или помещен в систему управления версиями.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Пользовательских параметров решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Решения](../../extensibility/internals/solutions.md)
