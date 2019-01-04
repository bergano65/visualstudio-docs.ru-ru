---
title: Реализация генераторов одного файла | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 728a1748d4c78bd93bf827290404f65607076b6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847786"
---
# <a name="implementing-single-file-generators"></a>Реализация генераторов одного файла
Пользовательский инструмент — иногда называют генератором одного файла, можно использовать для расширения [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] систем в проекта [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Пользовательский инструмент — это компонент COM, который реализует <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. Через этот интерфейс, пользовательский инструмент преобразует одного входного файла в один выходной файл. Результат преобразования может быть исходный код, или любой другой выходной полезны. Два примера файлов пользовательский код, сформированный svcutil.exe, код, созданный в ответ на изменения в визуальный конструктор и файлы, созданные с помощью языка описания служб (WSDL).  
  
 Когда загружается пользовательское средство или сохраняется входной файл, система проекта вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> метод и передает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> интерфейс обратного вызова, при котором средство может сообщить о ходе своего выполнения пользователю.  
  
 Выходной файл, который создает пользовательский инструмент добавляется в проект с зависимостью от входного файла. Система проекта автоматически определяет имя выходного файла, на основе строки, возвращаемые реализацию пользовательского инструмента <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Необходимо реализовать пользовательский инструмент <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс. При необходимости поддержки пользовательских инструментов <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> интерфейс для получения сведений из источника, отличного от входного файла. В любом случае, прежде чем использовать пользовательский инструмент, его необходимо зарегистрировать в системе или в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] локального реестра. Дополнительные сведения о регистрации пользовательских инструментов см. в разделе [регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>См. также  
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)