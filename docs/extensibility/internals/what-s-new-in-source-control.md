---
title: Что нового в управлении исходным веществом в визуальной студии 2015 SDK Документы Майкрософт
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703398"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Что нового в управлении исходным источником для визуальной студии 2015 SDK

В [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], вы можете обеспечить глубоко интегрированное решение управления исходным источником путем реализации управления исходным элементом VSPackage. В этом разделе описаны особенности управления исходным управлением VSPackages и представлен обзор шагов реализации.

## <a name="the-source-control-vspackage"></a>Источник управления VSPackage

Visual Studio поддерживает два типа решений управления исходным источником. Во всех версиях Visual Studio вы все еще можете интегрировать плагин на основе API-наосновения Source Control. Вы также можете создать VSPackage для управления исходным [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] сообщением, который обеспечивает глубокую интеграцию, путь, подходящий для решений управления исходным управлением, которые требуют высокого уровня сложности и автономии.

VSPackage может добавить практически любую функциональность в Visual Studio. Управление исходным элементом VSPackage обеспечивает полную функцию управления исходным интерфейсом для Visual Studio, от пользовательского интерфейса, представленного пользователю, до бэк-эндовой связи с системой управления исходным сообщением.

Реализация управления исходным элементом VSPackage требует стратегии «все или ничего». Создатель управления исходным интерфейсом VSPackage должен приложить значительные усилия в реализацию ряда интерфейсов управления исходным интерфейсом и новых элементов интерфейса (диалоговые коробки, меню и панели инструментов) для покрытия всей функциональности управления исходным источником, а также интерфейсов, необходимых для успешной интеграции любого пакета с Visual Studio.

Следующие шаги дают общий обзор того, что необходимо для реализации пакета управления исходным источником. Для получения [подробной](../../extensibility/internals/creating-a-source-control-vspackage.md)информации см.

1. Создайте VSPackage, который предлагает услуги управления частным иисточником.

2. Реализация интерфейсов в службах управления исходным элементом, предлагаемых Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> (например, интерфейс и интерфейс).

3. Зарегистрируйте элемент управления исходом VSPackage.

4. Реализуйте все элементы управления исходом, включая пункты меню, диалоговые поля, панели инструментов и контекстные меню.

5. Все события, связанные с контролем исходного кода, передаются в исходный контроль VSackage, когда он активен и должен обрабатываться вашим VSPackage.

6. Ваш исходный элемент управления VSPackage должен прослушивать события, такие как те, которые реализуют <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> интерфейс, а также события Track Project Document (TPD) (в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> интерфейса) и предпринять необходимые действия.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Обзор](../../extensibility/internals/source-control-integration-overview.md)
- [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)
