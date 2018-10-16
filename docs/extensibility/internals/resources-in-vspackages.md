---
title: Ресурсы в пакетах VSPackage | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d252f61a9f634f4bb8435626c41c586bbe5cb839
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130958"
---
# <a name="resources-in-vspackages"></a>Ресурсы в пакетах VSPackage
Локализованные ресурсы можно внедрять в собственном вспомогательные библиотеки DLL пользовательского интерфейса, управляемого вспомогательные библиотеки DLL, или в управляемом VSPackage сам.  
  
 Некоторые ресурсы не может быть внедрен в пакеты VSPackage. Можно внедрять управляемые следующие типы:  
  
-   Строки  
  
-   Ключи загрузки пакетов (которые также строки)  
  
-   Значки окна инструментов  
  
-   Скомпилированные файлы в таблицу выходные данные команды (CTO)  
  
-   Растровые изображения CTO  
  
-   Справка по командной строке  
  
-   О данных диалогового окна  
  
 Выбрано ресурсов в управляемых пакетов по идентификатору ресурса. Исключение — это файл CTO, который должен иметь имя CTMENU. Файл CTO должны отображаться в таблице ресурс как `byte[]`. Все прочие элементы ресурса идентифицируются по типу.  
  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> атрибут для указания [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] доступны, управляемые ресурсы.  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Установка <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> таким образом указывает, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] следует игнорировать неуправляемых библиотек спутниковой связи DLL при поиске ресурсов, например, с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обнаруживает два или более ресурсов, которые имеют тот же идентификатор ресурса, в нем первый ресурс, он находит.  
  
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
  
 Ниже приведен пример, как внедрять CTO байтового массива, которая должна быть названа CTMENU.  
  
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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] задержки загрузки пакетов VSPackage, когда это возможно. Вследствие того, что внедрения файла CTO в VSPackage является то, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо загружать такие пакеты VSPackage в памяти во время установки, являющийся при построении таблицы объединенные команд. Ресурсы можно извлечь из пакетов VSPackage с помощью проверки метаданных без выполнения кода в пакете VSPackage. VSPackage не инициализирован в данный момент сводится к минимуму снижение производительности.  
  
 Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запросы ресурс из VSPackage после установки, он скорее всего, уже загружены и инициализации, поэтому сводится к минимуму снижение производительности.  
  
## <a name="see-also"></a>См. также  
 [Управление пакетов VSPackage](../../extensibility/managing-vspackages.md)   
 [Локализованные ресурсы в приложениях MFC: вспомогательные библиотеки DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
