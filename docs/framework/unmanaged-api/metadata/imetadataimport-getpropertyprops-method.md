---
title: Метод IMetaDataImport::GetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: aded23e190de18d76bb2b9e2ffbae51cf2325419
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729230"
---
# <a name="imetadataimportgetpropertyprops-method"></a>Метод IMetaDataImport::GetPropertyProps

Возвращает метаданные для свойства, представленного указанным токеном.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a>Параметры  

 `prop`  
 окне Токен, представляющий свойство, для которого необходимо вернуть метаданные.  
  
 `pClass`  
 заполняет Указатель на маркер TypeDef, представляющий тип, реализующий свойство.  
  
 `szProperty`  
 заполняет Буфер для хранения имени свойства.  
  
 `cchProperty`  
 окне Размер в расширенных символах `szProperty` .  
  
 `pchProperty`  
 заполняет Число расширенных символов, возвращаемых в `szProperty` .  
  
 `pdwPropFlags`  
 заполняет Указатель на любые флаги атрибутов, применяемые к свойству. Это значение является битовой маской из перечисления [CorPropertyAttr](corpropertyattr-enumeration.md) .  
  
 `ppvSig`  
 заполняет Указатель на сигнатуру метаданных свойства.  
  
 `pbSig`  
 заполняет Число байтов, возвращенных в `ppvSig` .  
  
 `pdwCPlusTypeFlag`  
 заполняет Флаг, указывающий тип константы, которая является значением свойства по умолчанию. Это значение из перечисления Корелементтипе.  
  
 `ppDefaultValue`  
 заполняет Указатель на байты, в которых хранится значение по умолчанию для этого свойства.  
  
 `pcchDefaultValue`  
 заполняет Размер в расширенных символах `ppDefaultValue` , если `pdwCPlusTypeFlag` имеет ELEMENT_TYPE_STRING; в противном случае это значение не является значимым. В этом случае длина `ppDefaultValue` выводится из типа, заданного параметром `pdwCPlusTypeFlag` .  
  
 `pmdSetter`  
 заполняет Указатель на токен MethodDef, представляющий метод доступа set для свойства.  
  
 `pmdGetter`  
 заполняет Указатель на токен MethodDef, представляющий метод доступа get для свойства.  
  
 `rmdOtherMethod`  
 заполняет Массив токенов MethodDef, которые представляют другие методы, связанные со свойством.  
  
 `cMax`  
 [in] Максимальный размер массива `rmdOtherMethod`. Если массив не является достаточно большим, чтобы вместить все методы, они пропускаются без предупреждения.  
  
 `pcOtherMethod`  
 заполняет Число токенов MethodDef, возвращаемых в `rmdOtherMethod` .  
  
## <a name="requirements"></a>Требования  

 **Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).  
  
 **Заголовок:** COR. h  
  
 **Библиотека:** Включается в качестве ресурса в MsCorEE.dll  
  
 **.NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также раздел

- [Интерфейс IMetaDataImport](imetadataimport-interface.md)
- [Интерфейс IMetaDataImport2](imetadataimport2-interface.md)
