---
title: RDT_ReadLock использование (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb897fab61e1e14b52863b5853748c685200d5ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705932"
---
# <a name="rdt_readlock-usage"></a>Использование RDT_ReadLock

[_VSRDTFLAGS. RDT_ReadLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) — это флаг, который обеспечивает логику блокировки документа в таблице «Бегущий документ» (RDT), который представляет собой список всех документов, которые в настоящее время открыты в IDE Visual Studio. Этот флаг определяет, когда документы открыты, и является ли документ виден в пользовательском интерфейсе или удерживается незаметно в памяти.

Как правило, вы [используете _VSRDTFLAGS. RDT_ReadLock,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_ReadLock>) когда один из следующих истин:

- Вы хотите открыть документ незаметно и только читать, но это <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> еще не установлено, кто должен владеть им.

- Вы хотите, чтобы пользователю было предложено сохранить документ, который был невидимо открыт до того, как пользователь отобразил его в пользовательском интерфейсе, а затем попытался закрыть его.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Как управлять видимыми и невидимыми документами

Когда пользователь открывает документ в пользовательском <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейсе, должен быть установлен владелец документа и [_VSRDTFLAGS. RDT_EditLock](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS.RDT_EditLock>) флаг должен быть установлен. Если <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> владелец не может быть установлен, то документ не будет сохранен, когда пользователь нажимает **Сохранить все** или закрывает IDE. Это означает, что если документ открыт незаметно, когда он изменен в памяти, и пользователю предлагается сохранить `RDT_ReadLock` документ при выключении или сохранении, если **сохранено спасение всех,** то нельзя использовать. Вместо этого необходимо `RDT_EditLock` использовать и <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> зарегистрировать, когда [__VSREGDOCLOCKHOLDER. RDLH_WeakLockHolder](<xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER.RDLH_WeakLockHolder>) флаг.

## <a name="rdt_editlock-and-document-modification"></a>RDT_EditLock и модификация документов

Предыдущий флаг, упомянутый указывает на то, `RDT_EditLock` что невидимое открытие документа даст его, когда документ открыт пользователем в видимый **DocumentWindow**. Когда это происходит, пользователю предоставляется запрос **«Сохранить»** при закрытии видимого **Окна документа.** `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel`реализации, которые <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> используют службу, `RDT_ReadLock` изначально работают, когда берется только an (т.е. когда документ открывается незаметно для проверки информации). Позже, если документ должен быть изменен, то блокировка будет обновлена до слабого **RDT_EditLock.** Если пользователь открывает документ в видимом **DocumentWindow,**"слабый" `CodeModel` `RDT_EditLock` освобождается.

Если пользователь закрывает **DocumentWindow** и выбирает **Нет,** когда требуется сохранить `CodeModel` открытый документ, то реализация распоряжается всей информацией в документе и повторно открывает документ с диска незаметно при следующем времени, когда для документа требуется дополнительная информация. Тонкостью такого поведения является случай, когда пользователь открывает **DocumentWindow** невидимого открытого документа, изменяет его, закрывает его, а затем выбирает **Нет,** когда побуждение сохранить документ. В этом случае, если `RDT_ReadLock`документ имеет , то документ фактически не будет закрыт и измененный документ будет оставаться открытым незаметно в памяти, даже если пользователь решил не сохранять документ.

Если невидимое отверстие документа `RDT_EditLock`использует слабый, то он дает свой замок, когда пользователь открывает документ заметно и никаких других замков не удерживается. Когда пользователь закрывает **DocumentWindow** и выбирает **Нет,** когда предлагается сохранить документ, то документ должен быть закрыт из памяти. Это означает, что невидимый клиент должен прослушивать события RDT для отслеживания этого явления. В следующий раз, когда документ потребуется, документ должен быть вновь открыт.
