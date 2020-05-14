---
title: Модель языковой службы «Наследие» (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f024a02641902843f673ce3ff8583a4bce3b135
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707049"
---
# <a name="model-of-a-legacy-language-service"></a>Модель языковой службы прежних версий
Языковая служба определяет элементы и функции для определенного языка и используется для предоставления редактору информации, специфичной для этого языка. Например, редактор должен знать элементы и ключевые слова языка, чтобы поддержать окраску синтаксиса.

 Языковая служба тесно работает с буфером текста, управляемым редактором, и представлением, содержащим редактор. Опция Microsoft IntelliSense **Быстрая информация** является примером функции, предоставляемой языковой службой.

## <a name="a-minimal-language-service"></a>Минимальный языковой сервис
 Самая базовая языковая служба содержит следующие два объекта:

- *Языковая служба* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс. Языковая служба располагает информацией о языке, включая его имя, расширение имен файлов, менеджер оконного кода и кололизатор.

- *Раскрашиватель* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс.

  Следующий концептуальный рисунок показывает модель базовой языковой службы.

  ![Графический модель языкового сервиса](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel") Базовая модель языкового сервиса

  В окне документа размещается *представление* документа [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] редактора, в данном случае основного редактора. Представление документа и текстовый буфер принадлежат редактору. Эти объекты [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] работают с помощью специализированного окна документа, называемого *окном кода.* Окно кода содержится <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> в объекте, который создается и контролируется IDE.

  При загрузке файла с заданным расширением редактор находит языковую службу, связанную с <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> этим расширением, и передает ему окно кода, вызывая метод. Языковая служба возвращает *менеджерок оконного кода,* который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс.

  В следующей таблице приведен обзор объектов модели.

| Компонент | Объект | Функция |
|------------------| - | - |
| Текстовый буфер | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Unicode читать / писать текстовые потоки. Текст может использовать другие кодирования. |
| Окно кода | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Окно документа, содержащее одно или несколько текстовых представлений. Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] он находится в режиме интерфейса с несколькими документами (MDI), окно кода является ребенком MDI. |
| Текстовое представление | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Окно, которое позволяет пользователю перемещаться и просматривать текст с помощью клавиатуры и мыши. Текстовое представление отображается пользователю в качестве редактора. Можно использовать текстовые представления в обычных окнах редактора, окне вывода и немедленном окне. Кроме того, можно настроить один или несколько текстовых представлений в окне кода. |
| Текстовый менеджер | Управляется <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> службой, из которой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> вы получаете указатель | Компонент, который поддерживает общую информацию, разделяемую всеми описанными ранее компонентами. |
| Языковой сервис | Осуществление зависит; Реализует<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Объект, предоставляющий редактору информацию, специфичную для языка, такую как выделение синтаксиса, завершение оператора и соответствие скобки. |

## <a name="see-also"></a>См. также
- [Данные документа и представление документа в специализированных редакторах](../../extensibility/document-data-and-document-view-in-custom-editors.md)
