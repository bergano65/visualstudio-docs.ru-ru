---
title: Параметры контекста | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ea38b79be362f78fcc34161a480597fb0ecce40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727547"
---
# <a name="context-parameters"></a>Контекстные параметры
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) можно добавлять мастера в диалоговые окна **Новый проект**, **Добавить новый элемент**или **Добавить подпроект** . Добавленные мастера можно найти в меню **файл** или щелкнув правой кнопкой мыши проект в **Обозреватель решений**. Интегрированная среда разработки передает параметры контекста в реализацию мастера. Параметры контекста определяют состояние проекта, когда интегрированная среда разработки вызывает мастер.

 Интегрированная среда разработки запускает мастера, устанавливая флаг <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> в вызове в интегрированной среде разработки в метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> для проекта. Если этот параметр задан, проект должен вызвать выполнение метода `IVsExtensibility::RunWizardFile` с помощью зарегистрированного имени мастера или GUID и других контекстных параметров, которые среда IDE передает в нее.

## <a name="context-parameters-for-new-project"></a>Параметры контекста для нового проекта

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Тип мастера "зарегистрировано" (<xref:EnvDTE.Constants.vsWizardNewProject>) или GUID, указывающий тип мастера. В реализации [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] идентификатором GUID для мастера является {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Строка, которая является уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] именем проекта. |
| `LocalDirectory` | Локальное расположение рабочих файлов проекта. |
| `InstallationDirectory` | Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки. |
| `FExclusive` | Логический флаг, указывающий, что проект должен закрыть открытые решения. |
| `SolutionName` | Имя файла решения без части каталога или расширения *SLN* . Имя файла *suo* также создается с помощью `SolutionName`. Если этот аргумент не является пустой строкой, мастер использует <xref:EnvDTE._Solution.Create%2A> перед добавлением проекта с <xref:EnvDTE._Solution.AddFromTemplate%2A>. Если это имя является пустой строкой, используйте <xref:EnvDTE._Solution.AddFromTemplate%2A> без вызова <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Логическое значение, указывающее, должен ли мастер запускаться автоматически, как если бы была нажата кнопка **"Готово"** (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Параметры контекста для добавления нового элемента

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Тип мастера "зарегистрировано" (<xref:EnvDTE.Constants.vsWizardAddItem>) или GUID, указывающий тип мастера. В реализации [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] идентификатором GUID для мастера является {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Строка, которая является уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] именем проекта. |
| `ProjectItems` | Локальное расположение, содержащее рабочие файлы проекта. |
| `ItemName` | Имя добавляемого элемента. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит в диалоговом окне **Добавление элементов** . Имя основано на флагах, заданных в файле *VSDir* . Имя может иметь значение null. |
| `InstallationDirectory` | Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки. |
| `Silent` | Логическое значение, указывающее, должен ли мастер запускаться автоматически, как если бы была нажата кнопка **"Готово"** (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Параметры контекста для добавления подпроекта

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Тип мастера "зарегистрировано" (<xref:EnvDTE.Constants.vsWizardAddSubProject>) или GUID, указывающий тип мастера. В реализации [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] идентификатором GUID для мастера является {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Строка, которая является уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] именем проекта. |
| `ProjectItems` | Указатель на коллекцию `ProjectItems`, в которой работает мастер. Этот указатель передается мастеру на основе выбора иерархии проекта. Пользователь обычно выбирает папку, в которую следует поместить элемент, а затем вызывает диалоговое окно **Добавление элемента** проекта. |
| `LocalDirectory` | Локальное расположение рабочих файлов проекта. |
| `ItemName` | Имя добавляемого элемента. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит в диалоговом окне **Добавление элементов** . Имя основано на флагах, заданных в файле *VSDir* . Имя может иметь значение null. |
| `InstallationDirectory` | Путь к каталогу установки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| `Silent` | Логическое значение, указывающее, должен ли мастер запускаться автоматически, как если бы была нажата кнопка **"Готово"** (`TRUE`). |

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Параметры контекста для запуска мастеров](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)