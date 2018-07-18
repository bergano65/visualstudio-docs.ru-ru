---
title: Решение (. Файл SLN) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73d6f7fb83e9420f59122135761ce44ea641fe57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133410"
---
# <a name="solution-sln-file"></a>Решение (. Файл SLN)
Решение — это структура, для организации проектов в Visual Studio. Решение хранит сведения о состоянии для проектов в SLN (текстовый, общие) и файлы .suo (решения двоичный, пользовательские параметры). Дополнительные сведения о SUO-файлы в разделе [пользовательских параметров решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Если в результате, на которую ссылается SLN-файл загружается VSPackage, среда вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> для чтения в SLN-файл.  
  
 SLN-файл содержит сведения, основанные на тексте, в среде используется для поиска и загрузки параметров имя значение для материализованных данных и пакеты VSPackage, он ссылается на проект. При открытии решения среды циклический перебор `preSolution`, `Project`, и `postSolution` сведения в SLN-файл для загрузки решения, проекты в решении, а все сохраненные сведения присоединен в решение.  
  
 Файл каждый проект содержит дополнительные сведения, полученные с помощью среды для заполнения иерархии с элементами этого проекта. Сохранение иерархии данных управляется проектом; данные не хранятся обычно в SLN-файл, несмотря на то, что намеренно может записывать информацию проекта в SLN-файл, если вы решите сделать это. Дополнительные сведения, относящиеся к сохраняемости см. в разделе [долговременного хранения проекта](../../extensibility/internals/project-persistence.md) и [открытия и сохранения элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).  
  
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
  
 Чтобы загрузить решение, среде выполняет следующую последовательность задач.  
  
1.  Среде считывает общий раздел SLN-файл и обрабатывает все разделы, помеченные `preSolution`. В этом случае является одним из таких операторов:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Когда считывает среды `GlobalSection('name')` тега, он сопоставляет имя VSPackage с помощью реестра. Имя ключа должны присутствовать в реестре в разделе [HKLM\\< корневой раздел реестра для идентификатора приложения\>\SolutionPersistence\AggregateGUIDs]. Значение по умолчанию ключей — идентификатор GUID пакета (REG_SZ) VSPackage, записавшей записи.  
  
2.  Среде загрузки VSPackage, вызовы `QueryInterface` в VSPackage для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> интерфейса, а также вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> метод с данными в разделе, чтобы пакет VSPackage можно было хранить данные. Среды этот процесс повторяется для каждого `preSolution` раздела.  
  
3.  Среде итерацию проекта несохраняемые блоки. В этом случае имеется один проект.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Эта инструкция содержит уникальный идентификатор GUID проекта и GUID типа проекта. Эта информация используется в среде для поиска файла проекта или файлы, принадлежащие к решению и VSPackage необходимых для каждого проекта. Идентификатор GUID, переданный для проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> для загрузки конкретного VSPackage, относящиеся к проекту, выберите проект загружен в пакете VSPackage. В этом случае пакет VSPackage, который загружается для данного проекта — Visual Basic.  
  
     Каждый проект может сохранить проект уникальный идентификатор экземпляра, чтобы он был доступен при необходимости, другие проекты в решении. Если в системе управления версиями решений и проектов, путь к проекту желательно относительно пути к решению. При первой загрузке решения файлы проекта не может быть на компьютере пользователя. Наличие файла проекта, хранящиеся на сервере относительно файла решения, — относительно простой для файл проекта, чтобы найти и скопировать на компьютеры пользователей. А затем копирует и загружает все файлы, необходимые для проекта.  
  
4.  Среды, исходя из информации, содержащейся в разделе проекта SLN-файл, загружает каждого файла проекта. Затем сам проект отвечает за заполнение иерархии проекта и загрузка любых вложенных проектов.  
  
5.  После обработки всех разделов SLN-файл, решение отображается в обозревателе решений и готов для изменения пользователем.  
  
 Если не удается загрузить, любой VSPackage, реализующий проекта в решении <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> вызывается метод и получает возможность отменить изменения, которые могут были внесены во время загрузки каждого проекта в решении. При возникновении ошибки синтаксического анализа, как можно больше информации сохраняется файлы решений и среде отображает диалоговое окно предупреждение о повреждении решения.  
  
 При сохранении или закрытии решения <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> метод вызывается и передается в иерархию, чтобы увидеть, были ли внесены изменения с решением, должны быть введены в SLN-файл. Значение null, передаваемые в `QuerySaveSolutionProps` в <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, указывает, что сведения о сохраняются для решения. Если значение не равно null, сохраненной информации — для конкретного проекта, определяются указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейса.  
  
 Если сведения для сохранения, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> интерфейс вызывается с указателем <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> метод. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Средой для получения пары «имя значение» из затем вызывается метод `IPropertyBag` интерфейса и записывать данные SLN-файл.  
  
 `SaveSolutionProps` и `WriteSolutionProps` объекты, называются рекурсивно средой для получения сведений, которые будут сохраняться с `IPropertyBag` интерфейс, пока все изменения были введены в SLN-файл. Таким образом можно гарантировать, что данные будут сохранены с решения и доступных очередном открытии решения.  
  
 Чтобы увидеть, если у него есть все, чтобы сохранить SLN-файл перечисляется каждого загруженного пакета VSPackage. Это только во время загрузки, получат разделов реестра. Среде знает о загруженных пакетов, так как они находятся в памяти во время сохранения решения.  
  
 Только SLN-файл содержит записи в `preSolution` и `postSolution` разделы. Существуют не подобных разделов в файл SUO так, как это решение использует эту информацию для правильной загрузки. SUO-файл содержит параметры конкретного пользователя, например частных заметок, которые не предназначены для общих или поместить в системе управления версиями.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Пользовательских параметров решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Решения](../../extensibility/internals/solutions.md)