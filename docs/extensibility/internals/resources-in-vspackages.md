---
title: "Ресурсы в VSPackages | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 23
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 184642501b9452566a15e1aba30312e17500f7bb
ms.lasthandoff: 02/22/2017

---
# <a name="resources-in-vspackages"></a>Ресурсы в пакеты VSPackage
Локализованные ресурсы можно внедрять в собственном вспомогательные библиотеки DLL пользовательского интерфейса, управляемых вспомогательных библиотек DLL или в управляемом VSPackage сам.  
  
 Некоторые ресурсы не может быть внедрен в пакеты VSPackage. Следующие управляемые типы могут быть внедрены:  
  
-   Строки  
  
-   Ключи загрузки пакетов (которые также строки)  
  
-   Значки окна инструментов  
  
-   Скомпилированные файлы выходные данные команды таблицы (CTO)  
  
-   Руководитель технологического ОТДЕЛА компании растровые изображения  
  
-   Справка командной строки  
  
-   О данных диалогового окна  
  
 Выделенные ресурсы в управляемых пакетов идентификатор ресурса. Исключение файла руководитель технологического ОТДЕЛА компании, которая должна называться CTMENU. Руководитель технологического ОТДЕЛА компании файл должен указываться в таблице ресурсов как `byte[]`. Другие элементы ресурса идентифицируются по типу.  
  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>атрибут для указания [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] что управляемые ресурсы доступны.</xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>  
  
 [!code-cs[#1 VSSDKResources](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources&#1;](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Параметр <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>Указывает, что при таком [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] следует игнорировать неуправляемых библиотек спутниковой связи DLL при поиске ресурсов, например, с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> </xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обнаруживает два или более ресурсы, которые имеют тот же идентификатор ресурса, используется первый ресурс, он находит.  
  
## <a name="example"></a>Пример  
 Следующий пример представляет управляемый значок окна инструментов.  
  
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
  
 Следующий пример демонстрирует внедрение байтового массива руководитель технологического ОТДЕЛА компании, которая должна быть названа CTMENU.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]задержки загрузки пакетов VSPackages, когда это возможно. Вследствие внедрения файла руководитель технологического ОТДЕЛА компании в VSPackage является то, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо загружать такие пакеты VSPackage в памяти во время установки, являющийся при построении команды объединенные таблицы. Ресурсы могут быть извлечены из VSPackage, проверив метаданные без выполнения кода в VSPackage. VSPackage не инициализирован в данный момент, сводится к минимуму снижение производительности.  
  
 Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запросы ресурсов из VSPackage после установки этого пакета скорее всего уже загружены и инициализации, сводится к минимуму снижение производительности.  
  
## <a name="see-also"></a>См. также  
 [Управляемых пакетов VSPackages](../../misc/managed-vspackages.md)   
 [Управление пакеты VSPackage](../../extensibility/managing-vspackages.md)   
 [Локализованные ресурсы в приложениях MFC: вспомогательные библиотеки DLL](http://msdn.microsoft.com/Library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Управляемые пакеты VSPackage](../../misc/managed-vspackages.md)
