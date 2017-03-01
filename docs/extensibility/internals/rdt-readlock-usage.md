---
title: "Использование RDT_ReadLock | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: e7575b914f0645882f3570bdbe29221f2f8130cc
ms.openlocfilehash: a8ea44ef2dea3b3c4ebd29cf95b1886e2028e2c3
ms.lasthandoff: 02/22/2017

---
# <a name="rdtreadlock-usage"></a>Использование RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>представляет собой флаг, который предоставляет логику для блокировки документа на в под управлением документа таблицы (RDT), которого является список всех документов, открытых в Интегрированной среде разработки Visual Studio.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Этот флаг определяет при открытии документов и является ли документ видимым в пользовательском интерфейсе или принудительное незаметно в памяти.

Как правило, следует использовать <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>когда верно одно из следующих:</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

- Если требуется открыть документ незаметно и только для чтения, но он еще не установлен, которой <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>должен принадлежать его.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

- Если необходимо, чтобы пользователю запрос на сохранение документа, незаметно был открыт, прежде чем он отображается в пользовательском Интерфейсе пользователя и затем была предпринята попытка закрыть его.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Управление видимым и невидимым документов

Когда пользователь открывает документ в пользовательском Интерфейсе <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Владелец документа должно быть установлено и <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>должен быть установлен флаг.</xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> </xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Если не <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>владелец может быть установлено, а затем не сохранятся при щелчке **сохранить все** или закрывает IDE.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Это означает, что если документ открыт незаметно там, где он изменяется в памяти, и пользователю будет предложено сохранить документ при завершении работы или при сохранении Если **сохранить все** выбран, то `RDT_ReadLock` не может использоваться. Вместо этого необходимо использовать `RDT_EditLock` и зарегистрируйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>при <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER>флаг.</xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> </xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder>

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock и изменение документа

Упомянутые предыдущем флаг указывает, что даст невидимым открытия документа его `RDT_EditLock` при открытии документа пользователем в видимое **DocumentWindow**. В этом случае пользователь будет предложен **Сохранить** приглашение по видимых **DocumentWindow** закрывается. <xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel>реализации, используемые <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager>Служба изначально работать, только если `RDT_ReadLock` берется (т. е. когда документ открыт незаметно для анализа информации о).</xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager></xref:Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel> Позже, если необходимо изменить документ, затем блокировки будет обновлена до слабого **RDT_EditLock**. Если пользователь затем открывает документ в видимое **DocumentWindow**, `CodeModel`слабые `RDT_EditLock` освобождается.

Если пользователь закрывает **DocumentWindow** и выбирает **нет** при запросе сохраните открытый документ, то `CodeModel` реализация удаляет всю информацию в документе и незаметно открывается документ с диска при очередном Дополнительные сведения не требуются для документа. Тонкости этого поведения является экземпляром, когда пользователь открывает **DocumentWindow** невидимым открытого документа, его изменение, закрывает его и затем выбирает **нет** при появлении запроса на сохранение документа. В этом случае, если документ имеет `RDT_ReadLock`документ фактически не закрывается и измененный документ остается открытым незаметно в памяти, несмотря на то, что пользователь не был сохранен в документе.

Если невидимым открытия документа использует слабого `RDT_EditLock`, а затем возвращает его блокировки, когда пользователь открывает документ визуально и нет других блокировки удерживаются. Когда пользователь закрывает **DocumentWindow** и выбирает **нет** при появлении запроса на сохранение документа, затем документ должен быть закрыт из памяти. Это означает, что невидимым клиент должен прослушивать события RDT отслеживать этот экземпляр. Очередного документа является обязательным, его необходимо повторно.
