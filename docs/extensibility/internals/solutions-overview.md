---
title: "Обзор решений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 10
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
ms.openlocfilehash: 06ca562112b8b6feb711219502e3d10b1cb6f462
ms.lasthandoff: 02/22/2017

---
# <a name="solutions-overview"></a>Обзор решений
Решение — это группа из одного или нескольких проектов, работающих совместно для создания приложения. Проекта и состояние сведения, относящиеся к решению, хранятся в двух файлах другое решение. Файл решения (SLN), основанные на тексте можно поместить в системе управления версиями и совместно использоваться пользователями. Файл решения пользовательских параметров (.suo) в двоичные. В результате SUO-файл не может быть помещен в систему управления версиями и содержит сведения о пользователе.  
  
 Любой VSPackage можно написать для любого типа файла решения. Из-за природы файлы существует два различных интерфейсов, реализованных для их записи. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>Интерфейс записывает текстовые данные SLN-файл и <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>интерфейс записывает файл SUO двоичные потоки.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>  
  
> [!NOTE]
>  Проект не должен явно добавить запись для себя в файл решения; среда обработки, для проекта. Таким образом Если вы хотите добавить дополнительное содержимое в частности к файлу решения, необходимо зарегистрировать VSPackage таким образом.  
  
 Каждый VSPackage, поддержка сохраняемости решение использует три интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>интерфейс, который реализуется с помощью среды и вызывается VSPackage, и `IVsPersistSolutionProps` и `IVsPersistSolutionOpts`, обе реализации элементов по VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> `IVsPersistSolutionOpts` Только интерфейс должен быть реализован при личных сведений для записи VSPackage SUO-файл.  
  
 При открытии решения, процесс выполняется.  
  
1.  Среды считывает решения.  
  
2.  Обнаружив среды `CLSID`, он загружает соответствующий пакет VSPackage.  
  
3.  Если VSPackage загружается, среда вызывает `QueryInterface` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>интерфейса для интерфейса, который требует VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>  
  
    1.  При чтении из файла с расширением SLN, среда вызывает `QueryInterface` для `IVsPersistSolutionProps`.  
  
    2.  При чтении из файла .suo среда вызывает `QueryInterface` для `IVsPersistSolutionOpts`.  
  
 Конкретные сведения, относящиеся к использованию этих файлов можно найти в [решения (. Файл SLN)](../../extensibility/internals/solution-dot-sln-file.md) и [пользовательских параметров решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Если вы хотите создать новую конфигурацию решения, состоящий из двух проектов конфигураций и исключение в третьем из сборки, необходимо использовать свойство пользовательского интерфейса страницы или автоматизации. Нельзя изменить диспетчер конфигураций построения решений и их свойств непосредственно, но можно управлять с помощью диспетчера построения решения `SolutionBuild` класс в модели автоматизации DTE. Дополнительные сведения о настройке решений см. в разделе [конфигурация решения](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
