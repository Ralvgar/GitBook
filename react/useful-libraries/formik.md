# Formik

Formik is an easy to use library that lets us add forms to a React with form validation without the hassle of handling form values ourselves.

Also, it will return form validation errors automatically so that we don’t have to deal with them ourselves.

The hooks that come with Formik give us more flexibility with how we can create our forms in a React app.

An example of code from my project Beach sport rent:

```typescript
const formikInitialValues = {
  email: '',
  password: '',
  phoneNumber: '',
  passwordConfirm: '',
};

const formikValidationSchema = Yup.object({
  email: Yup.string()
    .email('Se requiere un email valido')
    .required('Se requiere un email'),
  phoneNumber: Yup.number().required('Debes introducir un numero de telefono'),
  password: Yup.string()
    .min(6, 'La contraseña debe tener al menos 6 caracteres')
    .required('Se requiere una contraseña'),
  passwordConfirm: Yup.string()
    .oneOf([Yup.ref('password'), null], 'Las contraseñas no coinciden')
    .required('Se requiere confirmar la contraseña'),
});

// ...

              <Formik
              initialValues={formikInitialValues}
              validationSchema={formikValidationSchema}
              onSubmit={(values, { setSubmitting, resetForm }) => {
                onClickOnSignUp(
                  values.email,
                  values.phoneNumber,
                  values.password
                );
                resetForm();
                setSubmitting(false);
              }}>
              {({ touched, errors }: FormikProps<FormValues>) => (
                <Form className='form-validate'>
                  <div className='form-group'>
                    <label className='form-label' htmlFor='loginUsername'>
                      Dirección email
                    </label>
                    <Field
                      className={classnames(`form-control`, {
                        'is-invalid': touched.email && errors.email,
                      })}
                      name='email'
                      id='loginUsername'
                      type='text'
                      placeholder='nombre@direccion.com'
                    />
                    {touched.email && errors.email && (
                      <div className='invalid-feedback'>{errors.email}</div>
                    )}
                  </div>
                  <div className='form-group'>
                    <label className='form-label' htmlFor='phoneNumber'>
                      Numero de telefono
                    </label>
                    <Field
                      className={classnames(`form-control`, {
                        'is-invalid': touched.phoneNumber && errors.phoneNumber,
                      })}
                      name='phoneNumber'
                      id='phoneNumber'
                      type='tel'
                      placeholder=' '
                    />
                    {touched.phoneNumber && errors.phoneNumber && (
                      <div className='invalid-feedback'>
                        {errors.phoneNumber}
                      </div>
                    )}
                  </div>
                  <div className='form-group'>
                    <label className='form-label' htmlFor='loginPassword'>
                      Contraseña
                    </label>
                    <Field
                      className={classnames(`form-control`, {
                        'is-invalid': touched.password && errors.password,
                      })}
                      name='password'
                      id='loginPassword'
                      placeholder='Contraseña'
                      type='password'
                    />
                    {touched.password && errors.password && (
                      <div className='invalid-feedback'>{errors.password}</div>
                    )}
                  </div>
                  <div className='form-group mb-4'>
                    <label
                      className='form-label'
                      htmlFor='loginPasswordConfirm'>
                      Confirme su contraseña
                    </label>
                    <Field
                      className={classnames(`form-control`, {
                        'is-invalid':
                          touched.passwordConfirm && errors.passwordConfirm,
                      })}
                      name='passwordConfirm'
                      id='loginPasswordConfirm'
                      placeholder='Repita su contraseña'
                      type='password'
                    />
                    {touched.passwordConfirm && errors.passwordConfirm && (
                      <div className='invalid-feedback'>
                        {errors.passwordConfirm}
                      </div>
                    )}
                  </div>
                  <button className='btn btn-lg btn-block btn-primary'>
                    Registrarse
                  </button>
                  <hr
                    className='my-3 hr-text letter-spacing-2'
                    data-content='También puede'
                  />
                  <button
                    className='btn btn btn-outline-primary btn-block btn-social mb-3'
                    type='button'>
                    <i className='fa-2x fa-facebook-f fab btn-social-icon'> </i>{' '}
                    Conectar con Facebook
                  </button>
                  <button
                    className='btn btn btn-outline-muted btn-block btn-social mb-3'
                    type='button'>
                    <i className='fa-2x fa-google fab btn-social-icon'> </i>{' '}
                    Conectar con Google
                  </button>
                  <hr className='my-4' />
                  <p className='text-sm text-muted'>
                    Al registrarse usted acepta los
                    <Link href='/'>
                      <a href='#'> Términos y condiciones </a>
                    </Link>{' '}
                    y la
                    <Link href='/'>
                      <a href='#'> Politica de privacidad</a>
                    </Link>
                    .
                  </p>
                </Form>
              )}
            </Formik>

```



{% embed url="https://formik.org/" %}





