---
title: Структура VSPackage (пакет VSPackage управления версиями) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03b9d4fb6a92694df55d6732ac80d75645209a87
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071282"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Структура VSPackage (пакет VSPackage системы управления версиями)

Пакет SDK для пакета управления для источника предоставляет рекомендации по созданию пакетов VSPackage, который позволяет разработчику элемента управления источника интегрировать свой функции системы управления версиями со средой Visual Studio. VSPackage — это компонент COM, который обычно загружается по запросу по среде разработки Visual Studio (IDE), на основе служб, которые объявляются с помощью пакета в записи в реестр. Каждый пакет VSPackage должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. VSPackage обычно потребляет служб, предоставляемых Visual Studio IDE и предлагает некоторые службы.

VSPackage объявляет элементами меню и устанавливает состояние элемента по умолчанию с помощью файла .vsct. Интегрированной среде разработки Visual Studio отображает элементы меню в этом состоянии до загрузки VSPackage. Как следствие, реализацию VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод вызывается для включения или отключения пунктов меню.

## <a name="source-control-package-characteristics"></a>Характеристик пакета управления источника

Пакет VSPackage системы управления версиями тесно интегрирована в Visual Studio. Семантика VSPackage включают:

- Интерфейс, реализуемый размещению VSPackage ( `IVsPackage` интерфейс)

- Реализация команды пользовательского интерфейса (vsct-файл и реализации <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс)

- Регистрация VSPackage с помощью Visual Studio.

Система управления версиями VSPackage должны обмениваться данными с этих сущностей Visual Studio:

- Проекты

- Редакторы

- Решения

- Windows

- В таблице выполняющихся документов

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Службы среды Visual Studio, которые могут включать

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider Service

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP интерфейсы реализованы и вызывается

Пакет системы управления версиями является VSPackage, и поэтому она может напрямую взаимодействовать с других пакетов VSPackage, должны быть зарегистрированы с помощью Visual Studio. Чтобы обеспечить доступ ко всем возможностям функции системы управления версиями, системы управления версиями VSPackage могут работать с интерфейсов, предоставляемых платформой проектов или оболочки.

Каждый проект в Visual Studio должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> распознается как проект интегрированной среды разработки Visual Studio. Тем не менее, этот интерфейс не является специальным достаточно для системы управления версиями. Проекты, которые должны быть под источником управления реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Этот интерфейс используется системой управления версиями VSPackage для запроса проекта за их содержимое и предоставлять его глифы и сведения о привязке (сведения, необходимые для установления соединения между расположением сервера и расположение проекта, который находится под на диске Система управления версиями).

Системы управления версиями, VSPackage реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, который в свою очередь позволяет проектам регистрироваться для системы управления версиями и получить их состояние глифов.

Полный список интерфейсов, которые необходимо учитывать VSPackage системы управления версиями, см. в разделе [связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>См. также

- [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Связанные службы и интерфейсы](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)