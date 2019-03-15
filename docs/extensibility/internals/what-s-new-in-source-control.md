---
title: Новые возможности системы управления версиями в Visual Studio SDK 2015 г. | Документация Майкрософт
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b667a6c6322a925b49290ab3234788a4eee3544
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867964"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Новые возможности в систему управления версиями для пакета SDK для Visual Studio 2015

В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], может обеспечить решение управления интегрирована источника путем реализации пакета VSPackage системы управления версиями. В этом разделе описаны возможности системы управления версиями пакетов VSPackage и общие сведения о реализации действий.

## <a name="the-source-control-vspackage"></a>Пакет VSPackage управления версиями

Visual Studio поддерживает два типа решений управления версиями. Во всех версиях Visual Studio, можно интегрировать основанная на API подключаемых модулей управления источник подключаемого модуля. Вы также можете создать VSPackage для системы управления версиями, предоставляющий глубокого интеграции [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] подходит для решений управления версиями, для которых требуется высокий уровень квалификации и независимость.

VSPackage может добавлять практически любые функциональные возможности для Visual Studio. Пакет VSPackage системы управления версиями предоставляет возможность управления полный исходный для Visual Studio с помощью пользовательского интерфейса, представленные пользователю обмена данными между серверной части с системой управления версиями.

Для реализации пакета VSPackage системы управления версиями требуется стратегию «все или ничего». Создатель пакета VSPackage системы управления версиями необходимо инвестировать значительный объем трудозатрат на применение нескольких интерфейсов управления источника и новых элементов пользовательского интерфейса (диалоговые окна, меню и панелей инструментов) для охвата всей системы управления версиями, а также интерфейсы для успешной интеграции с Visual Studio требуется любого пакета.

Следующие действия предоставляют общие сведения о необходимых для реализации пакет системы управления версиями. Дополнительные сведения см. в разделе [Создание пакета VSPackage управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Создайте пакет VSPackage, который предоставляет определенную службу частного исходного элемента управления.

2. Реализовывать интерфейсы в связанные с управлением версиями службы источника, которые являются окраски, предлагаемых Visual Studio (например, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> интерфейс).

3. Регистрация пакета VSPackage системы управления версиями.

4. Реализуйте все системы управления версиями пользовательского интерфейса, включая элементы меню, диалоговых окон, панелей инструментов и контекстные меню.

5. Все источника события, связанные с управлением версиями передаются VSackage системы управления версиями, когда он активен и должны обрабатываться VSPackage.

6. Пакет VSPackage системы управления версиями необходимо прослушивать событий, например реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> интерфейс, а также события отслеживания проекта документа (TPD) (как реализованный <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейс) и выполните необходимые действия.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Обзор](../../extensibility/internals/source-control-integration-overview.md)
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)