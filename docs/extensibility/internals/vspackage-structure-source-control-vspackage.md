---
title: Структура VSPackage (Управление источником VSPackage) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703810"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Структура VSPackage (пакет VSPackage системы управления версиями)

Пакет управления исходным управлением SDK содержит рекомендации по созданию VSPackage, которые позволяют исполнителю управления исходным источником интегрировать свою функциональность управления исходным источником с средой Visual Studio. VSPackage — это компонент COM, который обычно загружается по требованию интегрированной средой разработки Visual Studio (IDE) на основе услуг, рекламируемых пакетом в его регистрационных записях. Каждый VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>должен реализоваться. VSPackage обычно потребляет услуги, предлагаемые Visual Studio IDE и предлагает некоторые услуги самостоятельно.

VSPackage объявляет свои элементы меню и устанавливает состояние элемента по умолчанию через файл .vsct. Визуальная студия IDE отображает пункты меню в этом состоянии до загрузки VSPackage. Впоследствии реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода VSPackage называется для включения или отключания элементов меню.

## <a name="source-control-package-characteristics"></a>Характеристики пакета управления исходом

Управление источником VSPackage глубоко интегрировано в Visual Studio. Семантика VSPackage включает в себя:

- Интерфейс, который будет реализован в силу `IVsPackage` того, что VSPackage (интерфейс)

- Реализация команды uI (.vsct файл <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> и реализация интерфейса)

- Регистрация VSPackage с Visual Studio.

Управление исходным элементом VSPackage должно общаться с другими объектами Visual Studio:

- Проекты

- Редакторы

- Решения

- Windows

- Работая таблица документов

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Визуальные студии окружающей среды услуг, которые могут быть использованы

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider Службы

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Интерфейсы VSIP реализованы и вызваны

Пакет управления исходным источником является VSPackage, и поэтому он может взаимодействовать непосредственно с другими VSPackages, которые зарегистрированы в Visual Studio. Для того, чтобы обеспечить полную ширину функциональности управления исходным источником, управление исходным элементом VSPackage может иметь дело с интерфейсами, предоставляемыми проектами или оболочкой.

Каждый проект в <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio должен быть реализован в качестве проекта в рамках Visual Studio IDE. Однако этот интерфейс недостаточно специализирован для управления исходным источником. Проекты, которые, как ожидается, будут находиться под контролем источников реализации. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Этот интерфейс используется диспетчером VSPackage для запроса проекта для его содержимого и предоставления ему глифов и связывающей информации (информация, необходимая для установления связи между местоположением сервера и расположением диска проекта, напавшем под контроль источника).

Источник управления VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>реализует, что, в свою очередь, позволяет проектам зарегистрироваться для управления исходным источником и получить их статус глифов.

Для полного списка интерфейсов, которые должен учитывать элемент управления исходным элементом VSPackage, [см.](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

## <a name="see-also"></a>См. также

- [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
