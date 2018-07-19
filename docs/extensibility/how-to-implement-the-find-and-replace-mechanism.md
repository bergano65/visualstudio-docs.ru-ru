---
title: 'Практическое: реализовать найти и заменить механизм | Документация Майкрософт'
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45d0b1307d86b32f1def3c4474e1ca25959915c0
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056450"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Практическое: реализовать найти и заменить механизм

Visual Studio предоставляет два способа реализации поиска и замены. Рекомендуется передать образ текста в оболочку и позвольте ей выполнить поиск, выделение и замену текста. Это позволяет пользователям указывать несколько текстовых диапазонов. Кроме того пакет VSPackage может контролирует эти функциональные возможности, сам. В обоих случаях необходимо уведомить оболочки о текущего целевого объекта и целевые объекты для всех открытых документах.

## <a name="to-implement-findreplace"></a>Для реализации поиска и замены

1. Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> интерфейса на одном из объектов, возвращенных свойства рамки <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView> или <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>. Если вы создаете настраиваемый редактор, следует реализовать этот интерфейс как часть класса настраиваемого редактора.

2. Используйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> метод для указания параметров, которые ваш редактор поддерживает и указать, реализует ли поиск образа.

   Если ваш редактор поддерживает поиск изображений, реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.

   В противном случае реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.

3. Если вы реализуете <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> методы, чтобы упростить поиск задач путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> интерфейс.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>