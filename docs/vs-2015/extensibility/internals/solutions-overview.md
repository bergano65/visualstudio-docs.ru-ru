---
title: Обзор решений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb3bb85ab172404262c147cce285cebaf756afc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843232"
---
# <a name="solutions-overview"></a>Обзор решений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Решение — это группа из одного или нескольких проектов, совместно работающих с созданием приложения. Сведения о проекте и состоянии, относящиеся к решению, хранятся в двух разных файлах решений. Файл решения (SLN) основан на тексте и может размещаться под управлением исходного кода и совместно использоваться пользователями. Файл параметров пользователя решения (. suo) является двоичным. В результате файл. suo не может быть помещен в систему управления исходным кодом и содержит сведения, относящиеся к пользователю.  
  
 Любой пакет VSPackage может выполнять запись в любой тип файла решения. Из-за особенностей этих файлов для записи в них можно использовать два разных интерфейса. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>Интерфейс записывает текстовую информацию в файл. sln, и <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> интерфейс записывает двоичные потоки в файл. suo.  
  
> [!NOTE]
> Проекту не обязательно явно записывать запись в файл решения; среда обрабатывает этот проект. Таким образом, если вы не хотите добавлять дополнительное содержимое специально для файла решения, вам не нужно регистрировать пакет VSPackage таким образом.  
  
 Каждый пакет VSPackage, поддерживающий сохраняемость решения, использует три интерфейса — <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> интерфейс, который реализуется средой и вызывается пакетом VSPackage, а также `IVsPersistSolutionProps` и `IVsPersistSolutionOpts` , которые реализуются пакетом VSPackage. `IVsPersistSolutionOpts`Интерфейс должен быть реализован только в том случае, если частная информация должна быть записана пакетом VSPackage в suo-файл.  
  
 При открытии решения выполняется следующий процесс.  
  
1. Среда считывает решение.  
  
2. Если среда находит, то `CLSID` загружает соответствующий пакет VSPackage.  
  
3. Если загружен пакет VSPackage, среда вызывает `QueryInterface` интерфейс для интерфейса, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> который необходим для пакета VSPackage.  
  
   1. При чтении из файла. sln среда вызывает метод `QueryInterface` для `IVsPersistSolutionProps` .  
  
   2. При чтении из файла SUO среда вызывает метод `QueryInterface` для `IVsPersistSolutionOpts` .  
  
   Конкретные сведения об использовании этих файлов можно найти в [решении (. SLN) файл](../../extensibility/internals/solution-dot-sln-file.md) и [пользовательские параметры решения (. Файл SUO)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
> Если вы хотите создать новую конфигурацию решения, состоящую из двух конфигураций проектов и исключая треть из сборки, необходимо использовать пользовательский интерфейс страниц свойств или автоматизацию. Нельзя изменить конфигурации диспетчера сборки решения и их свойства напрямую, но можно управлять диспетчером сборки решения с помощью `SolutionBuild` класса из dte в модели автоматизации. Дополнительные сведения о настройке решений см. в разделе [Конфигурация решения](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
