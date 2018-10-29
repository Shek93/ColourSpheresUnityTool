# ColourSpheresUnityTool
Unity Tool made for a university project.

//CODE STARTS HERE
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEditor;

public class ToolWindow : EditorWindow {


    Vector3 WorldPos;
    Vector3 SphereSize;
    Color SphereColor;
    [MenuItem("Window/OurFirstTool")]
    public static void ShowWindow()
    {
        GetWindow<ToolWindow>("OurFirstWindow");
    }

    private void OnGUI()
    {
        WorldPos = EditorGUILayout.Vector3Field("Sphere World Position", WorldPos);
        SphereSize = EditorGUILayout.Vector3Field("Sphere Size", SphereSize);
        SphereColor = EditorGUILayout.ColorField("Sphere Color", SphereColor);

        if(GUILayout.Button("Create New Sphere"))
        {

            CreateSphere();
            
        }
    }

    void CreateSphere()
    {
        GameObject MySphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        
        MySphere.transform.position = WorldPos;
        MySphere.transform.localScale = SphereSize;
        Renderer SphereRenderer = MySphere.GetComponent<Renderer>();
        if (SphereRenderer != null)
        {
            SphereRenderer.material.color = SphereColor;
        }
    }
}
