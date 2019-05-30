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
ms.openlocfilehash: 1ddbd8084da150e47fdbe350770ea5e6bdb7e28d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335593"
---
# <a name="context-parameters"></a>Контекстные параметры
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE), можно добавить к мастеров **новый проект**, **Добавление нового элемента**, или **добавить проект Sub** диалоговым окнам. Добавлена мастеров можно найти на **файл** меню или щелкнув правой кнопкой мыши проект в **обозревателе решений**. Интегрированной среды разработки параметры контекста передается в реализацию мастера. Параметры контекста определять состояние проекта при интегрированной среды разработки вызывает мастера.

 Мастера запуска среды IDE, задав <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг в вызове IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> метод для проекта. Если задано, проект, необходимо вызвать `IVsExtensibility::RunWizardFile` метод, который выполняется с помощью имя зарегистрированного мастера или идентификатор GUID и других параметров контекста, которые передает ему интегрированной среды разработки.

## <a name="context-parameters-for-new-project"></a>Контекстные параметры для нового проекта

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardNewProject>) или GUID, который указывает тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , идентификатор GUID для мастера реализуется {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта. |
| `LocalDirectory` | Локальное расположение работы файлы проекта. |
| `InstallationDirectory` | Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является установкой. |
| `FExclusive` | Логический флаг, который указывает, что проект должен закрыть открытые решения. |
| `SolutionName` | Имя файла решения без каталог или *.sln* расширения. *.Suo* также создается имя файла с помощью `SolutionName`. Если этот аргумент не является пустой строкой, то мастер использует <xref:EnvDTE._Solution.Create%2A> перед добавлением проекта с <xref:EnvDTE._Solution.AddFromTemplate%2A>. Если это имя является пустой строкой, используйте <xref:EnvDTE._Solution.AddFromTemplate%2A> без вызова <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Логическое значение, указывающее, следует ли автоматически запускать мастер так, как если **Готово** щелкают (`TRUE`). |

## <a name="context-parameters-for-add-new-item"></a>Контекстные параметры для добавления нового элемента

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardAddItem>) или GUID, который указывает тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , идентификатор GUID для мастера реализуется {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта. |
| `ProjectItems` | Локальное расположение, которое содержит проект рабочих файлов. |
| `ItemName` | Имя элемента, который должен быть добавлен. Это имя является имя файла по умолчанию или имя файла, который пользователь вводит из **добавить элементы** диалоговое окно. Имя основывается на флаги, которые были заданы в *.vsdir* файла. Имя может быть значение null. |
| `InstallationDirectory` | Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] является установкой. |
| `Silent` | Логическое значение, указывающее, следует ли автоматически запускать мастер так, как если **Готово** щелкают (`TRUE`). |

## <a name="context-parameters-for-add-sub-project"></a>Контекстные параметры для добавления проекта Sub

| Параметр | Описание |
|-------------------------| - |
| `WizardType` | Зарегистрированный тип мастера (<xref:EnvDTE.Constants.vsWizardAddSubProject>) или GUID, который указывает тип мастера. В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , идентификатор GUID для мастера реализуется {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Строка, являющаяся уникальным [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] имя проекта. |
| `ProjectItems` | Указатель на `ProjectItems` коллекции, на котором работает мастер. Этот указатель передается к мастеру, в зависимости от выбранной иерархии проекта. Пользователь обычно выбирает папку для размещения элемента, а затем вызывает проекта **Добавление элемента** диалоговое окно. |
| `LocalDirectory` | Локальное расположение работы файлы проекта. |
| `ItemName` | Имя элемента, который должен быть добавлен. Это имя является имя файла по умолчанию или имя файла, который пользователь вводит из **добавить элементы** диалоговое окно. Имя основывается на флаги, которые были заданы в *.vsdir* файла. Имя может быть значение null. |
| `InstallationDirectory` | Путь к каталогу [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] установки. |
| `Silent` | Логическое значение, указывающее, следует ли автоматически запускать мастер так, как если **Готово** щелкают (`TRUE`). |

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)
- [Мастера](../../extensibility/internals/wizards.md)
- [Файл мастера (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Контекстные параметры для запуска мастеров](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)