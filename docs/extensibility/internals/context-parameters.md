---
title: "Контекстные параметры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 143a8738f2eb6517c1642eafd2b9629e0fa8f84d
ms.lasthandoff: 02/22/2017

---
# <a name="context-parameters"></a>Параметры контекста
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE), можно добавить мастеров для **новый проект**, **Добавление нового элемента**, или **добавить проект Sub** диалоговые окна. Добавлены мастера доступны на **файл** меню или щелкнув правой кнопкой мыши проект в **обозревателе решений**. IDE передает параметры контекста реализации мастера. Параметры контекста определить состояние проекта, когда IDE вызывает мастер.  
  
 Мастера запуска среды IDE, задав <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>флаг в IDE вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>метод для проекта.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> </xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> При задании проекта необходимо вызвать `IVsExtensibility::RunWizardFile` метод для выполнения с помощью зарегистрированных мастера имя или идентификатор GUID и других параметров контекста, которые передает интегрированной среды разработки.  
  
## <a name="context-parameters-for-new-project"></a>Контекстные параметры для нового проекта  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardNewProject>) или идентификатор GUID, указывающий тип мастера.</xref:EnvDTE.Constants.vsWizardNewProject> В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D0-4999-11D1-B6D1-00A0C90F2744} — реализация GUID для мастера.|  
|`ProjectName`|Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта.|  
|`LocalDirectory`|Локальная папка работы файлов проекта.|  
|`InstallationDirectory`|Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки.|  
|`FExclusive`|Логический флаг, который указывает, что проект следует закрывать открытые решения.|  
|`SolutionName`|Имя файла решения без каталог или расширения SLN-файл. Имя файла SUO также создается с помощью `SolutionName`. Если этот аргумент не является пустой строкой, мастер использует <xref:EnvDTE._Solution.Create%2A>перед добавлением проекта с <xref:EnvDTE._Solution.AddFromTemplate%2A>.</xref:EnvDTE._Solution.AddFromTemplate%2A> </xref:EnvDTE._Solution.Create%2A> Если это имя является пустой строкой, используйте <xref:EnvDTE._Solution.AddFromTemplate%2A>без вызова <xref:EnvDTE._Solution.Create%2A>.</xref:EnvDTE._Solution.Create%2A> </xref:EnvDTE._Solution.AddFromTemplate%2A>|  
|`Silent`|Логическое значение, указывающее, должен ли мастер выполняться без вмешательства пользователя, если **Готово** щелкают (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Контекстные параметры для добавления нового элемента  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardAddItem>) или идентификатор GUID, указывающий тип мастера.</xref:EnvDTE.Constants.vsWizardAddItem> В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D1-4999-11D1-B6D1-00A0C90F2744} — реализация GUID для мастера.|  
|`ProjectName`|Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта.|  
|`ProjectItems`|Локальное расположение, которое содержит проект рабочих файлов.|  
|`ItemName`|Имя элемента, который требуется добавить. Это имя является именем файла по умолчанию или имя файла, который пользователь из **добавить элементы** диалоговое окно. Имя основано на флаги, которые заданы в VSDir-файл. Имя может иметь значение null.|  
|`InstallationDirectory`|Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки.|  
|`Silent`|Логическое значение, указывающее, должен ли мастер выполняться без вмешательства пользователя, если **Готово** щелкают (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Параметры контекста для проекта добавить Sub  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardAddSubProject>) или идентификатор GUID, указывающий тип мастера.</xref:EnvDTE.Constants.vsWizardAddSubProject> В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] {0F90E1D2-4999-11D1-B6D1-00A0C90F2744} — реализация GUID для мастера.|  
|`ProjectName`|Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта.|  
|`ProjectItems`|Указатель на `ProjectItems` коллекции, на котором работает мастер. Такой указатель передается для мастера, основанного на выбранной иерархии проекта. Пользователь обычно выбирает папку для размещения элемента, а затем вызывает проекта **добавить элемент** диалоговое окно.|  
|`LocalDirectory`|Локальная папка работы файлов проекта.|  
|`ItemName`|Имя элемента, который требуется добавить. Это имя является именем файла по умолчанию или имя файла, который пользователь из **добавить элементы** диалоговое окно. Имя основано на флаги, которые заданы в VSDir-файл. Имя может иметь значение null.|  
|`InstallationDirectory`|Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки.|  
|`Silent`|Логическое значение, указывающее, должен ли мастер выполняться без вмешательства пользователя, если **Готово** щелкают (`TRUE`).|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)   
 [Мастера](../../extensibility/internals/wizards.md)   
 [Мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Контекстные параметры для запуска мастеров](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
