---
title: Параметры контекста Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709308"
---
# <a name="context-parameters"></a>Контекстные параметры
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) можно добавить мастера в **новый проект,** **добавить новый элемент**или добавить диалоговые ящики **Sub Project.** Добавленные мастера доступны в меню **файла** или при нажатии правого нажатия на проект в **Solution Explorer.** IDE передает параметры контекста в реализацию мастера. Параметры контекста определяют состояние проекта, когда IDE вызывает мастера.

 IDE запускает мастера, установив <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг в вызове IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> к методу проекта. При наборе проект должен `IVsExtensibility::RunWizardFile` вызвать выполнение метода с помощью зарегистрированного имени мастера или GUID и других параметров контекста, которые IDE передает ему.

## <a name="context-parameters-for-new-project"></a>Параметры контекста для нового проекта

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип<xref:EnvDTE.Constants.vsWizardNewProject>мастера () или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации, GUID для мастера является "0F90E1D0-4999-11D1-B6D1-00A0C90F2744". |
| `ProjectName` | Строка, которая [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является уникальным названием проекта. |
| `LocalDirectory` | Локальное расположение рабочих файлов проекта. |
| `InstallationDirectory` | Путь каталога [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является установкой. |
| `FExclusive` | Флаг Boolean, указывающий на то, что проект должен закрывать открытые решения. |
| `SolutionName` | Название файла решения без части каталога или расширения *.sln.* Имя *файла .suo* также `SolutionName`создается с помощью . Если этот аргумент не является пустой <xref:EnvDTE._Solution.Create%2A> строкой, <xref:EnvDTE._Solution.AddFromTemplate%2A>мастер использует перед добавлением проекта с . Если это имя является пустой строкой, используйте <xref:EnvDTE._Solution.AddFromTemplate%2A> без вызова <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Boolean, что указывает ли мастер должен **Finish** работать молча,`TRUE`как если бы закончить нажали ( ). |

## <a name="context-parameters-for-add-new-item"></a>Параметры контекста для добавления нового элемента

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип<xref:EnvDTE.Constants.vsWizardAddItem>мастера () или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации, GUID для мастера является "0F90E1D1-4999-11D1-B6D1-00A0C90F2744". |
| `ProjectName` | Строка, которая [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является уникальным названием проекта. |
| `ProjectItems` | Локальное местоположение, содержащее рабочие файлы проекта. |
| `ItemName` | Имя элемента, который должен быть добавлен. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит из диалогового окна **Add Items.** Название основано на флагах, которые установлены в файле *.vsdir.* Имя может быть нулевая стоимость. |
| `InstallationDirectory` | Путь каталога [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является установкой. |
| `Silent` | Boolean, что указывает ли мастер должен **Finish** работать молча,`TRUE`как если бы закончить нажали ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Параметры контекста для проекта Add Sub

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип<xref:EnvDTE.Constants.vsWizardAddSubProject>мастера () или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] реализации, GUID для мастера является "0F90E1D2-4999-11D1-B6D1-00A0C90F2744". |
| `ProjectName` | Строка, которая [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является уникальным названием проекта. |
| `ProjectItems` | Указатель на `ProjectItems` коллекцию, на которой работает мастер. Этот указатель передается мастеру на основе выбора иерархии проектов. Пользователь обычно выбирает папку, в которой можно поместить элемент, а затем вызывает диалоговую окно **добавленного элемента** проекта. |
| `LocalDirectory` | Локальное расположение рабочих файлов проекта. |
| `ItemName` | Имя элемента, который должен быть добавлен. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит из диалогового окна **Add Items.** Название основано на флагах, которые установлены в файле *.vsdir.* Имя может быть нулевая стоимость. |
| `InstallationDirectory` | Каталог путь установки. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] |
| `Silent` | Boolean, что указывает ли мастер должен **Finish** работать молча,`TRUE`как если бы закончить нажали ( ). |

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл Мастера (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Параметры контекста для запуска мастеров](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
