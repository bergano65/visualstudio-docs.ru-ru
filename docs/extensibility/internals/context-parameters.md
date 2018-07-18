---
title: Параметры контекста | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb6646e917b4cb94b4cd0534b513d148490cf69d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132108"
---
# <a name="context-parameters"></a>Параметры контекста
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE), можно добавить мастеров для **новый проект**, **Добавление нового элемента**, или **добавьте подпроекта** диалоговым окнам. Добавлены мастеров доступны на **файл** меню или щелкнув правой кнопкой мыши проект в **обозревателе решений**. Интегрированной среды разработки передает параметры контекста для реализации мастера. Параметры контекста определить состояние проекта, когда IDE вызывает мастер.  
  
 Мастера запуска интегрированной среды разработки, задав <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг в вызове IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод для проекта. Если задано, проект необходимо вызвать `IVsExtensibility::RunWizardFile` метод для выполнения с помощью зарегистрированного мастер имя или идентификатор GUID и других параметров контекста, которые передает интегрированной среды разработки.  
  
## <a name="context-parameters-for-new-project"></a>Контекстные параметры для нового проекта  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardNewProject>) или идентификатор GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации, идентификатор GUID для мастера — {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта.|  
|`LocalDirectory`|Локальное расположение рабочие файлы проекта.|  
|`InstallationDirectory`|Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] процесса установки.|  
|`FExclusive`|Логический флаг, указывающий, что проект следует закрыть открытые решения.|  
|`SolutionName`|Имя файла решения без каталог или расширения .sln. Имя файла SUO также создается с помощью `SolutionName`. Если этот аргумент не является пустой строкой, мастер использует <xref:EnvDTE._Solution.Create%2A> перед добавлением проекта с <xref:EnvDTE._Solution.AddFromTemplate%2A>. Если это имя является пустой строкой, используйте <xref:EnvDTE._Solution.AddFromTemplate%2A> без вызова <xref:EnvDTE._Solution.Create%2A>.|  
|`Silent`|Логическое значение, указывающее, следует ли автоматически запускать мастер как если бы **Готово** щелкают (`TRUE`).|  
  
## <a name="context-parameters-for-add-new-item"></a>Параметры контекста для добавления нового элемента  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardAddItem>) или идентификатор GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации, идентификатор GUID для мастера — {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта.|  
|`ProjectItems`|Локальное расположение, которое содержит проект рабочих файлов.|  
|`ItemName`|Имя элемента, который требуется добавить. Это имя является имя файла по умолчанию или имя файла, который пользователь из **добавить элементы** диалоговое окно. Имя основан на флаги, которые заданы в VSDir-файл. Имя может иметь значение null.|  
|`InstallationDirectory`|Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] процесса установки.|  
|`Silent`|Логическое значение, указывающее, следует ли автоматически запускать мастер как если бы **Готово** щелкают (`TRUE`).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Параметры контекста для добавления проекта Sub  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardAddSubProject>) или идентификатор GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации, идентификатор GUID для мастера — {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}.|  
|`ProjectName`|Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта.|  
|`ProjectItems`|Указатель на `ProjectItems` коллекции, на котором работает мастер. Такой указатель передается мастер, в зависимости от выбранной иерархии проекта. Пользователь обычно выбирает папку для размещения элемента, а затем вызывает проекта **добавить элемент** диалоговое окно.|  
|`LocalDirectory`|Локальное расположение рабочие файлы проекта.|  
|`ItemName`|Имя элемента, который требуется добавить. Это имя является имя файла по умолчанию или имя файла, который пользователь из **добавить элементы** диалоговое окно. Имя основан на флаги, которые заданы в VSDir-файл. Имя может иметь значение null.|  
|`InstallationDirectory`|Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] процесса установки.|  
|`Silent`|Логическое значение, указывающее, следует ли автоматически запускать мастер как если бы **Готово** щелкают (`TRUE`).|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)   
 [Мастеры](../../extensibility/internals/wizards.md)   
 [Мастер (. Файл VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Контекстные параметры для запуска мастеров](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)