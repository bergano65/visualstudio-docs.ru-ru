---
title: Модель языковой службы прежних | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 381c5b37cdc5d8a166003bdf7dd931dd95e6dcb3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943093"
---
# <a name="model-of-a-legacy-language-service"></a>Модель языковой службы прежних версий
Языковая служба определяет элементы и функции для конкретного языка и используется для предоставления редактора с информацией для данного языка. Например редактор должен знать, элементы и ключевые слова языка для поддержки выделения синтаксиса цветом.  
  
 Языковая служба тесно сотрудничает с текстовым буфером, управляется редактора и представления, которая содержит редактор. Microsoft IntelliSense **краткие сведения** параметр является примером возможность, предоставляемая языковой службы.  
  
## <a name="a-minimal-language-service"></a>Услуга минимальный язык  
 Самая базовая служба языка содержит следующие два объекта:  
  
- *Языковая служба* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс. Языковая служба содержит сведения о языке, включая его имя, расширения имен файлов, диспетчер окон кода и палитры.  
  
- *Палитры* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс.  
  
  Ниже концептуальной показаны модель службу языка basic.  
  
  ![График языка модели службы](../../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
  Модель службы языка Basic  
  
  Узлы окно документа *представление документа* редактора, в данном случае [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базовым редактором. Представление документа и текстовый буфер, принадлежат редактора. Эти объекты работают с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] через окно документа в специализированных вызывается *окно кода*. Окно кода содержится в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объект, который создается и управляется интегрированной среды разработки.  
  
  При загрузке файла с помощью данного расширения, редактора находит языковую службу, связанную с этим расширением и передает ему окно кода, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод. Служба возвращает язык *диспетчер окон кода*, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс.  
  
  Ниже приведены общие сведения о объектов в модели.  
  
| Компонент | Object | Функция |
|------------------| - | - |
| Текстовый буфер | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Чтение и запись текстовый поток в Юникоде. Существует возможность текст для использования в других кодировках. |
| Окно кода | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Окно документа, который содержит один или несколько представлений текста. Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] находится в режиме многодокументного интерфейса (MDI) в окне кода является дочерней формы MDI. |
| Представление текста | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Окно, которое позволяет пользователю перейти и просмотреть текст с помощью клавиатуры и мыши. Текст отображается для пользователя как редактор. Можно использовать представления текста в windows обычный редактор, окно вывода и окно "Интерпретация". Кроме того можно настроить одно или несколько представлений текста в окне кода. |
| Диспетчер текста | Управляет <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> службы, из которого можно получить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> указатель | Компонент, который совместно используется всеми компонентами, описанные ранее общей информации. |
| языковая служба | Реализация зависит от того; реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Объект, реализующий редактор с информацией конкретного языка, например выделение синтаксиса, завершение операторов и парные фигурные скобки. |
  
## <a name="see-also"></a>См. также  
 [Данные документа и представление документа в специализированных редакторах](../../extensibility/document-data-and-document-view-in-custom-editors.md)