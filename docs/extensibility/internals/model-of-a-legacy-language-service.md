---
title: Модель языковой службы прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b87106060d3fd66b3659f5d49159ebbb9be9ef6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726376"
---
# <a name="model-of-a-legacy-language-service"></a>Модель языковой службы прежних версий
Языковая служба определяет элементы и функции для конкретного языка и используется для предоставления редактора со сведениями, характерными для этого языка. Например, редактору необходимо получить сведения об элементах и ключевых словах языка для поддержки цветов синтаксиса.

 Языковая служба тесно взаимодействует с текстовым буфером, который управляется редактором, и представлением, содержащим редактор. Параметр **краткие сведения** Microsoft IntelliSense — это пример функции, предоставляемой языковой службой.

## <a name="a-minimal-language-service"></a>Минимальная языковая служба
 Самая базовая языковая служба содержит два следующих объекта:

- *Языковая служба* реализует интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>. Языковая служба содержит сведения о языке, включая его имя, расширения имен файлов, диспетчер окон кода и тонированный цвет.

- В области *выделения реализуется* интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.

  На следующем концептуальном рисунке показана модель базовой языковой службы.

  ![График модели языковой службы](../../extensibility/media/vslanguageservicemodel.gif "вслангуажесервицемодел") Модель языковой службы Basic

  В окне документа размещается *представление документа* редактора, в данном случае это редактор [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Core. Представление документа и текстовый буфер принадлежат редактору. Эти объекты работают с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] через специализированное окно документа, называемое *окном кода*. Окно кода содержится в объекте <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>, который создается и управляется интегрированной средой разработки.

  При загрузке файла с заданным расширением редактор находит языковую службу, связанную с этим расширением, и передает ее в окно кода, вызывая метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>. Языковая служба возвращает *Диспетчер окон кода*, который реализует интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>.

  В следующей таблице приведены общие сведения об объектах в модели.

| Компонент | Object | Функция |
|------------------| - | - |
| Текстовый буфер | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Поток текста для чтения и записи в Юникоде. В тексте можно использовать другие кодировки. |
| Окно кода | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Окно документа, содержащее одно или несколько текстовых представлений. Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] находится в режиме многодокументного интерфейса (MDI), окно кода является дочерним элементом MDI. |
| Текстовое представление | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Окно, позволяющее пользователю перемещаться по тексту и просматривать его с помощью клавиатуры и мыши. Текстовое представление отображается для пользователя в виде редактора. Текстовые представления можно использовать в обычных окнах редактора, в окне вывода и в окне интерпретации. Кроме того, можно настроить одно или несколько текстовых представлений в окне кода. |
| Диспетчер текста | Управляется службой <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>, из которой можно получить указатель <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> | Компонент, который поддерживает общие сведения, общие для всех описанных выше компонентов. |
| Языковая служба | Зависит от реализации; реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Объект, предоставляющий редактору сведения о конкретном языке, такие как выделение синтаксиса, завершение операторов и сопоставление фигурных скобок. |

## <a name="see-also"></a>См. также
- [Данные документа и представление документа в специализированных редакторах](../../extensibility/document-data-and-document-view-in-custom-editors.md)