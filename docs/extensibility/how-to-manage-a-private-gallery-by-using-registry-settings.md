---
title: 'Как: Управление частной галереей с помощью настроек реестра (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710932"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Как: Управление частной галереей с помощью настроек реестра
Если вы являетесь администратором или разработчиком изолированного расширения Shell, вы можете управлять доступом к элементам управления, шаблонам и инструментам в галерее Visual Studio, галерее образцов или частных галереях. Чтобы сделать галерею доступной или недоступной, создайте файл *.pkgdef,* описывающий измененные ключи реестра и их значения.

## <a name="manage-private-galleries"></a>Управление частными галереями
 Можно создать файл *.pkgdef* для управления доступом к галереям на нескольких компьютерах. Этот файл должен иметь следующий формат.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 Ключ `Repositories` относится к галерее, которая будет включена или отключена. Галерея Visual Studio и Галерея образцов используют следующие GUID-хранилища:

- Визуальная студия Галерея : 0F45E408-7995-4375-9485-86B8DB553DC9

- Образцы Галерея : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Значение `Disabled` не является обязательным. По умолчанию включена галерея.

  Значение `Priority` определяет порядок, в котором галереи перечислены в диалоговом окне **Опционов.** Visual Studio Gallery имеет приоритет 10, а Галерея образцов имеет приоритет 20. Частные галереи начинаются с приоритета 100. Если несколько галерей имеют одинаковое значение приоритета, порядок, в `DisplayName` котором они отображаются, определяется значениями их локализованных атрибутов.

  Значение `Protocol` требуется для галерей на основе Atom или SharePoint.

  Либо `DisplayName`, `DisplayNameResourceID` или `DisplayNamePackageGuid`оба и , должны быть указаны. Если все указано, `DisplayNameResourceID` `DisplayNamePackageGuid` то используется пара и пара.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Отключить галерею Visual Studio с помощью файла .pkgdef
 Вы можете отключить галерею в файле *.pkgdef.* Следующая запись отсутсвий Visual Studio Галерея:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 Следующая запись отравлишает образцов Галерея:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>См. также
- [Частные галереи](../extensibility/private-galleries.md)
