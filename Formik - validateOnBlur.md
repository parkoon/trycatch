## Formik - validateOnBlur

---

> AOS 에서 키보드가 내려가면서 `input` 아래에 있는 에러 메세지가 사라지는거 같은데, 에러 메세지 유지해주세요.

라고 QA 팀에서 요청이 왔다.

코드는 대충 아래와 같고, `onSubmit` 에서 닉네임 중복 체크를 하고 `helpers.setFieldError` 로 에러 메세지를 설정해주고 있었다.

```javascript
<Formik
  initialValues={initialValues}
  onSubmit={handleProfileCreate}
  validationSchema={validationSchema}
>
  {({ errors, touched, isSubmitting }) => {
    return (
      <S.ProfileInputForm>
        <S.FieldWrapper>
          <Field
            error={touched.nickname && errors.nickname}
            type="text"
            name="nickname"
            label="닉네임"
            as={Input}
            maxLength={12}
            focusOnMount
          />
        </S.FieldWrapper>
        ...
      </S.ProfileInputForm>
    );
  }}
</Formik>
```

`formik` 의 기본 validation 은 `validateOnBlur` 가 `true` 이다. 따라서, 가상 키보드가 내려가면서 `blur` 이벤트가 발생하고, `onSubmit` 에서 했던 중복처리가 빠지게된다.

그래서, `validateOnBlur={false}` 로 수정했다.
