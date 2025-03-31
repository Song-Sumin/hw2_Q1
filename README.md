# HW2_Q1 readme
## What you need
You need Visual Studio 2022 and window 11 OS.

And C/C++ should be available in VS2022.

## About
This project is about Phong Shading.
To view the result image, open result.png, 
and if you want an explanation of the code, scroll down below.

## How to run

1. Click code and download as zip file.
![image](https://github.com/user-attachments/assets/9b9c6e66-7f7d-4aeb-a093-bb1e542b034b)

2. Unzip a download file
![image](https://github.com/user-attachments/assets/6d1d1e3d-eff9-42f1-a719-32c5ae6ca80b)

3. Open hw2_Q1-master. Double click hw2_Q1-master and opne OpenglViewer.sln
![image](https://github.com/user-attachments/assets/7c0ca433-d940-42fd-a2a3-3893344c0344)


4. click "F5" on your keybord. Then you will get the result.
![image](https://github.com/user-attachments/assets/559d3c38-31c0-4d00-82d8-61836b1e78ec)

## Code explanation
```
vec3 lightPos(-4.0f, 4.0f, -3.0f);
vec3 lightColor(1.0f, 1.0f, 1.0f);
```
Set position of the light and color white.

-----------
```
	vec3 ka, kd, ks;
	float specularPower;
	virtual vec3 getNormal(const vec3& point) const = 0;
```
In class surface, declare vectors representing the material properties of an object:

ka: Ambient coefficient. This defines how much ambient light the material reflects.

kd: Diffuse coefficient. This defines how much diffuse light the material reflects.

ks: Specular coefficient. This defines how much specular light the material reflects.

specularPower define shininess of the specular hightlight.

get normal function return normal vector at that point.

![image](https://github.com/user-attachments/assets/81aa8f94-b64b-40e4-8832-9a341ba54165)

--------------
```
vec3 getNormal(const vec3& point) const override {
	return normalize(point - center);
}
Sphere(const vec3& c, float r, const vec3& ka, const vec3& kd, const vec3& ks, float specularPower)
	: center(c), radius(r) {
	this->ka = ka;
	this->kd = kd;
	this->ks = ks;
	this->specularPower = specularPower;
}
```
In Sphere and Plane class, overridden virtual funtion getNormal.

Read Ka, Kd, Ks and specularPower value

-------------
In Scene.trace funtion, 
```
if (hit_surface) {
	vec3 hitPoint = ray.origin + closest_t * ray.direction;
	vec3 normal = hit_surface->getNormal(hitPoint);
	return phongShading(ray, hitPoint, normal, *hit_surface);
}
```
