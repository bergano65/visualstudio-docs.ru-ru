---
title: Реализация генераторов одного файла | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30294f901f3e0536caeb84dc55af5630db24956a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557664"
---
# <a name="implementing-single-file-generators"></a>Реализация генераторов одного файла
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [реализация генераторов одного файла](https://docs.microsoft.com/visualstudio/extensibility/internals/implementing-single-file-generators).  
  
Пользовательский инструмент — иногда называют генератором одного файла, можно использовать для расширения [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] и [!INCLUDE[csprcs](../../includes/csprcs-md.md)] систем в проекта [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Пользовательский инструмент — это компонент COM, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. Через этот интерфейс, пользовательский инструмент преобразует одного входного файла в один выходной файл. Результат преобразования может быть исходный код, или любой другой выходной полезны. Два примера файлов пользовательский код, сформированный svcutil.exe, код, созданный в ответ на изменения в визуальный конструктор и файлы, созданные с помощью языка описания служб (WSDL).  
  
 Когда загружается пользовательское средство или сохраняется входной файл, система проекта вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> метод и передает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> интерфейс обратного вызова, при котором средство может сообщить о ходе своего выполнения пользователю.  
  
 Выходной файл, который создает пользовательский инструмент добавляется в проект с зависимостью от входного файла. Система проекта автоматически определяет имя выходного файла, на основе строки, возвращаемые реализацию пользовательского инструмента <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Необходимо реализовать пользовательский инструмент <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. При необходимости поддержки пользовательских инструментов <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> интерфейс для получения сведений из источника, отличного от входного файла. В любом случае, прежде чем использовать пользовательский инструмент, его необходимо зарегистрировать в системе или в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] локального реестра. Дополнительные сведения о регистрации пользовательских инструментов см. в разделе [регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>См. также  
 [Определение пространства имен по умолчанию проекта](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)

