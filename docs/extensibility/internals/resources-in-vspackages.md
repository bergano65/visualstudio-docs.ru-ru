---
title: Ресурсы в VSPackages Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705603"
---
# <a name="resources-in-vspackages"></a>Ресурсы в пакетах VSPackage
Вы можете вставлять локализованные ресурсы в местные спутниковые UI DLLs, управляемые спутниковые DLLs, или в управляемый VSPackage себя.

 Некоторые ресурсы не могут быть встроены в VSPackages. Следующие управляемые типы могут быть встроены:

- Строки

- Ключи загрузки пакета (которые также являются строками)

- Значки окна инструмента

- Составленные таблицы команд (CTO) файлы

- Биткарты cTO

- Помощь командной строки

- О данных диалогового окна

  Ресурсы в управляемом пакете выбираются идентификатором ресурсов. Исключением является файл cTO, который должен называться CTMENU. Файл cTO должен отображаться в `byte[]`таблице ресурсов как . Все остальные элементы ресурсов идентифицируются по типу.

  Можно использовать <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> атрибут, чтобы [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] указать, что доступны управляемые ресурсы.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Установка <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> таким образом [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] указывает на то, что следует игнорировать неуправляемые спутниковые <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>DLL при поиске ресурсов, например, с помощью . Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] они сталкиваются с двумя или более ресурсами с одинаковым идентификатором ресурсов, он использует первый ресурс, который он находит.

## <a name="example"></a>Пример
 Следующим примером является управляемое представление значка окна инструмента.

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

 Ниже приводится следующий пример, как вставлять массив байт cTO, который должен быть назван CTMENU.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]задержки загрузки VSPackages, когда это возможно. Следствием встраивания файла cTO в VSPackage является то, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо загрузить все такие VSPackages в память во время настройки, которая, когда он строит объединенную таблицу команд. Ресурсы могут быть извлечены из VSPackage путем изучения метаданных без запуска кода в VSPackage. В настоящее время VSPackage не инициализирован, поэтому потеря производительности минимальна.

 Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запрашивает ресурс из VSPackage после настройки, этот пакет, скорее всего, уже загружен и инициализирован, поэтому потеря производительности минимальна.

## <a name="see-also"></a>См. также
- [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
- [Локализованные ресурсы в приложениях MFC. Вспомогательные библиотеки DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
