---
title: Обзор решений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d64175c570c4fbca26bae0aa587b66e04cbee2be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="solutions-overview"></a>Общие сведения о решениях
Решение — это группа из одного или нескольких проектов, которые работают совместно, чтобы создать приложение. Проект и состояние сведения, относящиеся к решению, хранятся в двух файлах другого решения. Файл решения (SLN), основанные на тексте и могут находиться в системе управления исходным кодом и совместно использоваться пользователями. Файл решения пользовательских параметров (.suo) в двоичные. В результате SUO-файл не может быть помещен в системе управления версиями и содержит сведения о пользователе.  
  
 Любой пакет VSPackage можно написать для любого типа файла решения. Из-за особенностей файлы существует два различных интерфейсов, реализованных для их записи. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> Интерфейс записывает текстовые данные SLN-файл и <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс записывает двоичные потоки SUO-файл.  
  
> [!NOTE]
>  Проект не нужно явно добавить запись для себя в файле решения; среды, обрабатывает для проекта. Таким образом Если вы хотите добавить дополнительное содержимое специально для файла решения, регистрировать VSPackage в этом случае не нужно.  
  
 Каждый пакет VSPackage, поддержка сохраняемости решение использует три интерфейса <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> интерфейс, который реализуется с помощью среды и вызывается в пакете VSPackage, и `IVsPersistSolutionProps` и `IVsPersistSolutionOpts`, являющиеся, как реализована в пакете VSPackage. `IVsPersistSolutionOpts` Только интерфейс должен быть реализован, если закрытый сведения для записи в пакете VSPackage SUO-файл.  
  
 При открытии решения процесс выполняется.  
  
1.  Среде считывает решения.  
  
2.  Если находит среды `CLSID`, он загружает соответствующий пакет VSPackage.  
  
3.  Если пакет VSPackage загружается, среда вызывает метод `QueryInterface` для <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> интерфейса для интерфейса, который требуется пакет VSPackage.  
  
    1.  При чтении из SLN-файл, среда вызывает `QueryInterface` для `IVsPersistSolutionProps`.  
  
    2.  При чтении из файла .suo окружение вызывает `QueryInterface` для `IVsPersistSolutionOpts`.  
  
 Определенные сведения, относящиеся к использованию этих файлов можно найти в [решения (. Файл SLN)](../../extensibility/internals/solution-dot-sln-file.md) и [пользовательских параметров решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Если вы хотите создать новую конфигурацию решения, состоящий из двух проектов конфигураций и исключение третий из сборки, необходимо использовать пользовательский Интерфейс страниц свойств или автоматизации. Нельзя изменить их свойства и диспетчер конфигурации построения решений непосредственно, но можно управлять с помощью диспетчера построения решения `SolutionBuild` класса из DTE в модели автоматизации. Дополнительные сведения о настройке решения см. в разделе [конфигурации решения](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>