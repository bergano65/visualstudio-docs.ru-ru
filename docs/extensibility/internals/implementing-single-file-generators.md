---
title: "Реализация генераторов одного файла | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пользовательские инструменты, реализация"
  - "проекты [Visual Studio SDK] расширяемости"
  - "проекты [Visual Studio SDK], управляемые пользовательские инструменты"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Реализация генераторов одного файла
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Пользовательский инструмент \- иногда называемый генератор одиночных файлов \- может быть использовано для расширения [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] внутри системы проекта  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Пользовательский инструмент компонент COM, реализующий <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс.  Используя этот интерфейс, настраиваемый инструмент преобразует один входной файл в одновыходовой файл.  Результат преобразования может быть исходным кодом или любым другим выходом, который полезен.  2 Примера кода средство\-произведенных файлов пользовательские код, созданный в ответ на изменения в визуальном конструкторе и файлы, созданные с помощью языка WSDL.  
  
 Если пользовательский инструмент загрузке или сохранении входной файл, система проекта вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> метод и передает ссылку на a  <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> интерфейс обратного вызова, посредством которого средство может информировать ход его выполнения пользователю.  
  
 Выходной файл, пользовательское средство создает добавляется в проект с зависимостью во входном файле.  Система проекта автоматически определяет имя выходного файла, основанное на строке, возвращаемой реализацией настраиваемого средства <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Настраиваемое средство должно реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс.  При необходимости пользовательские средства поддерживают <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> интерфейс для получения данных из источников, за исключением входного файла.  В любом случае, прежде чем можно будет использовать пользовательский инструмент его необходимо зарегистрировать с помощью системы или в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] локальный реестр.  Дополнительные сведения о регистрации пользовательских средств см. в разделе [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md).  
  
## См. также  
 [Определение пространства имен по умолчанию для проекта](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Предоставление визуальные конструкторы типов](../../extensibility/internals/exposing-types-to-visual-designers.md)