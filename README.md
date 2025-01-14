# Konversi Model
## SavedModel
save_path = 'saved_model/'
tf.saved_model.save(model, save_path)

## TF-Lite
converter = tf.lite.TFLiteConverter.from_keras_model(model)
tflite_model = converter.convert()

with open('rice_model.tflite', 'wb') as f:
    f.write(tflite_model)

## TFJS
model.save('rice_model.h5')
!tensorflowjs_converter --input_format keras rice_model.h5 saved_models/tfjs_model
