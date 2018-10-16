---
title: Ресурсы в пакетах VSPackage | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 073245be91c1689d0dd70d30207dc4dd809c578e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188584"
---
# <a name="resources-in-vspackages"></a>Ресурсы в пакетах VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Локализованные ресурсы можно внедрять в собственном спутниковой связи DLL пользовательского интерфейса и управляемых вспомогательных библиотек DLL, или в управляемом VSPackage сам.  
  
 Некоторые ресурсы не может быть внедрен в пакетах VSPackage. Можно включить следующие управляемые типы:  
  
-   Строки  
  
-   Ключи загрузки пакетов (которые также являются строками)  
  
-   Значки окна средств  
  
-   Скомпилированные файлы таблицы выходных данных команды (CTO)  
  
-   Руководитель технологического ОТДЕЛА компании точечных рисунков  
  
-   Справка по командной строке  
  
-   О данных диалоговых окон  
  
 Ресурсы в управляемом пакете выбираются по идентификатору ресурса. Исключением является файл руководитель технологического ОТДЕЛА компании, которая должна быть названа CTMENU. Файл руководитель технологического ОТДЕЛА компании должен указываться в нее ресурсов, как `byte[]`. Все прочие элементы ресурсов идентифицируются по типу.  
  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> атрибут для указания [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] что управляемые ресурсы доступны.  
  
 [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
 [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
 Установка <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> указывает, что таким образом [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] должен игнорировать неуправляемых вспомогательные библиотеки DLL, при поиске ресурсов, например, с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Если [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] обнаруживает два или более ресурсов, которые имеют тот же идентификатор ресурса, используется первый ресурс, он находит.  
  
## <a name="example"></a>Пример  
 Следующий пример — это управляемое представление значка окна инструментов.  
  
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
  
 Ниже приведен пример, как внедрять руководитель технологического ОТДЕЛА компании байтового массива, которая должна быть названа CTMENU.  
  
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
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] задержки загрузки пакетов VSPackage, когда это возможно. Следствием внедрения файл руководитель технологического ОТДЕЛА компании в VSPackage является то, что [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] необходимо загрузить всех таких пакетов VSPackage в памяти во время установки, при построении команды объединенные таблицы. Ресурсы могут быть извлечены из VSPackage с помощью проверки метаданных без выполнения кода в VSPackage. В настоящее время VSPackage не инициализирован, поэтому снижение производительности сводится к минимуму.  
  
 Когда [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] запросы ресурс из VSPackage после завершения установки, он скорее всего, уже быть загружается и инициализируется, поэтому снижение производительности сводится к минимуму.  
  
## <a name="see-also"></a>См. также  
 [Управляемые пакеты VSPackage](../../misc/managed-vspackages.md)   
 [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)   
 [Локализованные ресурсы в приложениях MFC: вспомогательные библиотеки DLL](http://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Управляемые пакеты VSPackage](../../misc/managed-vspackages.md)

