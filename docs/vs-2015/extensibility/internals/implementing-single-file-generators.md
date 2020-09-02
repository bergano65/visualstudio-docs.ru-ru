---
title: Реализация генераторов с одним файлом | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192690"
---
# <a name="implementing-single-file-generators"></a>Реализация генераторов одного файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пользовательское средство, которое иногда называют генератором одиночных файлов, может использоваться для расширения [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] системы проектов и в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Пользовательский инструмент — это COM-компонент, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. С помощью этого интерфейса пользовательское средство преобразует один входной файл в отдельный выходной файл. Результатом преобразования может быть исходный код или любые другие полезные выходные данные. Два примера пользовательских файлов кода — это код, создаваемый в ответ на изменения в визуальном конструкторе и файлах, созданных с помощью языка описания веб-служб (WSDL).  
  
 При загрузке пользовательского инструмента или сохранении входного файла система проекта вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> метод и передает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> интерфейс обратного вызова, при котором средство может сообщить пользователю о ходе выполнения.  
  
 Выходной файл, формируемый настраиваемым инструментом, добавляется в проект с зависимостью от входного файла. Система проекта автоматически определяет имя выходного файла на основе строки, возвращаемой реализацией пользовательского инструмента <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Пользовательский инструмент должен реализовывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. При необходимости пользовательские инструменты поддерживают <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> интерфейс для получения сведений из источников, отличных от входного файла. В любом случае, прежде чем использовать пользовательский инструмент, необходимо зарегистрировать его в системе или в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] локальном реестре. Дополнительные сведения о регистрации пользовательских средств см. в разделе [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>См. также:  
 [Определение пространства имен по умолчанию для проекта](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)
