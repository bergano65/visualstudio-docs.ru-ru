---
title: Ресурсы в пакетах VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696090"
---
# <a name="resources-in-vspackages"></a>Ресурсы в пакетах VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Локализованные ресурсы можно внедрять в встроенные библиотеки DLL пользовательского интерфейса, управляемые вспомогательные библиотеки DLL или в самом управляемом пакете VSPackage.  
  
 Некоторые ресурсы не могут быть внедрены в пакеты VSPackage. Можно внедрить следующие управляемые типы:  
  
- Строки  
  
- Ключи загрузки пакета (которые также являются строками)  
  
- Значки окна инструментов  
  
- Скомпилированные файлы вывода командной таблицы (CTO)  
  
- Точечные рисунки CTO  
  
- Справка по командной строке  
  
- О данных диалоговых окон  
  
  Ресурсы в управляемом пакете выбираются по ИДЕНТИФИКАТОРу ресурса. Исключением является файл CTO, который должен иметь имя CTMENU. Файл CTO должен отображаться в таблице ресурсов как `byte[]` . Все остальные элементы ресурсов идентифицируются по типу.  
  
  Чтобы <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> указать [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , что управляемые ресурсы доступны, можно использовать атрибут.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Таким образом, этот параметр указывает, что [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] при поиске ресурсов следует пропускать неуправляемые вспомогательные библиотеки DLL, например с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Если [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] встречает два или больше ресурсов с одинаковым идентификатором ресурса, используется первый найденный ресурс.  
  
## <a name="example"></a>Пример  
 В следующем примере представлено управляемое представление значка окна инструментов.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 В следующем примере показано, как внедрить массив байтов CTO, который должен иметь имя CTMENU.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] При возможности задерживает загрузку пакетов VSPackage. Следствием внедрения файла CTO в VSPackage является то, что [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] должен загружать все такие пакеты VSPackage в памяти во время установки, то есть при построении Объединенной командной таблицы. Ресурсы можно извлечь из пакета VSPackage, проверив метаданные без выполнения кода в VSPackage. В настоящее время пакет VSPackage не инициализирован, поэтому снижение производительности является минимальным.  
  
 При [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] запросе ресурса из пакета VSPackage после установки этот пакет, скорее всего, уже загружен и инициализирован, поэтому снижение производительности будет минимальным.  
  
## <a name="see-also"></a>См. также:  
 [Управляемые пакеты VSPackage](../../misc/managed-vspackages.md)   
 [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)   
 [Локализованные ресурсы в приложениях MFC: вспомогательные библиотеки DLL](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Управляемые пакеты VSPackage](../../misc/managed-vspackages.md)
