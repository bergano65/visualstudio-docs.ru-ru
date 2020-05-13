---
title: Модель для пакетов управления исходом (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707074"
---
# <a name="model-for-source-control-packages"></a>Модель для пакетов системы управления версиями
Следующая модель представляет собой пример реализации управления исходным ресурсом. В модели вы видите интерфейсы, которые необходимо реализовать, и службы среды, которые необходимо вызвать. Как и все службы, вы на самом деле называют методы определенного интерфейса, который вы получаете с помощью службы. Имена классов определены, чтобы было легче увидеть, как осуществляется контроль источника.

 ![SCC&#95;примеры TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Пример проекта управления исходом

## <a name="interfaces"></a>Интерфейсы
 Вы можете реализовать элемент управления исходным интерфейсом для новых типов проектов в Visual Studio, используя список интерфейсов, показанных в следующей таблице.

|Интерфейс|Использовать|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Вызывается по проектам и редакторам, прежде чем они сохраняют или изменяют (грязные) файлы. Этот интерфейс доступен <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> с помощью службы.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Вызывается по проектам, чтобы запросить разрешение на добавление, удаление или переименование файла или каталога. Этот интерфейс также вызывается проектами для информирования среды, когда утвержденное действие добавить, удалить или переименовать действие завершено. Доступ к нему <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> осуществляется с помощью сервиса.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Реализовано любой организацией, которая регистрируется для уведомления при добавлении, переименовании или удалении файла или каталога. Чтобы зарегистрироваться для <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>уведомления о событии, позвоните .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Вызывается по проектам, чтобы зарегистрироваться в пакете управления исходным ресурсом и получить информацию о статусе управления исходным источником. Этот интерфейс доступен <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> с помощью службы.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Реализовано проектом для ответа на запросы управления исходными данными о файлах и получения параметров управления исходным элементом, необходимых для файла проекта.|

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
